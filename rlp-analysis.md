RLP(Recursive Linear Prefix)는 이더리움에서 노드들 끼리 데이터를 주고 받을 때 사용하는 인코딩 알고리즘입니다.
- 데이터를 직렬화/역직렬화하는데 사용되는 기본 인코딩 방법입니다.

이더리움은 트랜잭션, 블록, 스마트 컨트랙트와 같은 복잡한 데이터 구조를 이더리움 네트워크 내 저장 및 통신을 위해 바이너리 형식으로 인코딩/디코딩하기 위해 RLP를 사용합니다.

크게 2가지 용도로 사용합니다.

1. 인코딩: 이더리움은 네트워크를 통해 데이터를 전송하거나 블록체인에 저장하기 전에 데이터를 바이너리 형식으로 인코딩해야합니다. RLP는 데이터의 원래 구조를 보존하면서 효율적인 저장과 전송을 보장하는 방식으로 데이터 구조를 인코딩하는데 사용됩니다. 이렇게 인코딩된 데이터는 이더리움 네트워크를 통해 전송되거나 블록체인에 저장됩니다.
3. 디코딩: 블록체인에서 데이터를 검색하거나 네트워크를 통해 데이터를 수신할 때, 이더리움은 바이너리 표현을 원래 데이터 구조로 다시 디코딩해야합니다. RLP는 인코딩된 데이터를 디코딩하여 이더리움 애플리케이션에서 이해하고 처리할 수 있는 원래 데이터 구조로 재구성하는데 사용됩니다.

RLP Source code analysis

파일의 구조는 이렇습니다.

- decode_tail_test.go Decoder 테스트 코드
- decode_test.go Decoder 테스트 코드
- decode.go Decoder, decoding RLP 데이터를 GO의 데이터 구조로 변환을 구현한 코드
- doc.go : Document 코드
- encbuffer_example_test : Encoder 테스트 코드
- encbuffer.go : Encoder, GO의 데이터 구조를 RLP 데이터로 변환을 구현한 코드(버퍼에 쓰는 방법 제공)
- encode_test.go : Encoder 테스트 코드
- encode.go : Encoder, GO의 데이터 구조를 RLP 데이터로 변환을 구현한 코드(핵심 코드)
- encode_example_test.go : Encoder 테스트 코드
- iterator_test.go : Iterator 테스트 코드
- iterator.go : Iterator, RLP 데이터를 순회하는 코드
- raw_test.go : Raw 테스트 코드
- raw.go : RLP 값의 인코딩 및 디코딩과 관련된 다양한 유틸리티 함수 코드
- safe.go : 바이트 배열에서 바이트 슬라이스를 추출하는 함수 코드
- typecache.go : 인코더 함수와 디코더 함수를 유형별로 빠르게 찾기 위한 목적으로 사용하기 위해 구현된 코드
- unsafe.go : 안전하지 않은 방법으로 바이트 배열에서 바이트 슬라이스를 추출하는 함수 코드

### typecache.go 파일은 처리 중인 데이터 유형에 따라 인코더 및 디코더 함수의 캐싱 및 검색을 관리합니다.
Go는 함수 overloading이나 Generics을 지원하지 않으므로 typecache는 주어진 유형에 적합한 인코더 및 디코더 함수를 빠르게 찾는데 사용됩니다.

typecache.go의 핵심 데이터 구조는 typeCache Map으로 key 값은 type이고 value는 다양한 유형의 인코더 및 디코더 함수(typeinfo)입니다.
typeCache 구조체의 Key는 typekey* 구조체의 인스턴스입니다. 
typekey* 구조체에는 두 가지 구성 요소가 포함됩니다.

```go
type typekey struct {
	reflect.Type // 기본 Type를 나타냅니다.
	rlpstruct.Tags // 연관된 모든 구조체 태그를 나타냅니다.
}
```





typekey 구조체는 맵의 key로 사용되며, 구조체 태그가 다른 디코더 함수를 생성할 수 있으므로 모든 구조체 태그와 함께 type 자체를 포함합니다.
```go
type typeCache struct {
	cur atomic.Value

	// This lock synchronizes writers.
	mu   sync.Mutex
	next map[typekey]*typeinfo
}
```

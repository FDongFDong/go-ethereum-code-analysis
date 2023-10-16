```go
  type Transaction struct {
  	inner TxData    // Consensus contents of a transaction
  	time  time.Time // Time first seen locally (spam avoidance)
  
  	// caches
  	hash atomic.Value  // 트랜잭션 해시값
  	size atomic.Value
  	from atomic.Value  // 트랜잭션 발신자 주소
  }
```

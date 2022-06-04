```mermaid
flowchart TD
	subgraph sys-02[シャドウIT]
	  sys-02-pii-01[(めっちゃ大事なデータ)]<-->sys-02-pii-02[(大事なデータ)]<-->sys-02-etc-01[(それ以外)]
		sys-02-pii-01<-->sys-02-etc-01
	end
	sys-02-pii-01 <--> pii-01
	sys-02-pii-02 <--> pii-02
	sys-02-etc-01 <--> etc-01
	subgraph 管理下にあるIT環境
		subgraph sys-01[業務で許可されているシステム]
		  pii-01[(めっちゃ大事なデータ)]<-->pii-02[(大事なデータ)]<-->etc-01[(それ以外)]
			pii-01<-->etc-01
		end
	 	subgraph emp-01[従業員の会社デバイス]
			emp-01-pii-01[(めっちゃ大事なデータ)]<--> pii-01 & sys-02-pii-01
			emp-01-pii-02[(大事なデータ)]<-->pii-02 & sys-02-pii-02
			emp-01-etc-01[(それ以外)]<-->etc-01 & sys-02-etc-01
		end
		subgraph out-02[委託先へ貸与した会社デバイス]
			out-02-pii-01[(めっちゃ大事なデータ)]<----> pii-01 & sys-02-pii-01
			out-02-pii-02[(大事なデータ)]<-->pii-02 & sys-02-pii-02
			out-02-etc-01[(それ以外)]<-->etc-01 & sys-02-etc-01
		end
	end
	subgraph emp-02[従業員の私物デバイス]
				emp-02-pii-01[(めっちゃ大事なデータ)]<-------->|ブロックしたい| pii-01 & sys-02-pii-01
				emp-02-pii-02[(大事なデータ)]<-->|OKとするか|pii-02 & sys-02-pii-02
				emp-02-etc-01[(それ以外)]<-->etc-01 & sys-02-etc-01
	end
	subgraph out-01[委託先のデバイス]
			out-01-pii-01[(めっちゃ大事なデータ)]<------> pii-01 & sys-02-pii-01
			out-01-pii-02[(大事なデータ)]<-->pii-02 & sys-02-pii-02
			out-01-etc-01[(それ以外)]<-->etc-01 & sys-02-etc-01
	end
  ```

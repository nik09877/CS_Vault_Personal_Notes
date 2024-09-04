# Distributed Transactions

## 2 Phase Commit
- Transaction Coordinator manages the transactions / participants.
- Every participant knows each other and transaction coordinator knows about all.
- Prepare phase
	- After all the updates in microservices happen, it asks all of them are you ready to commit ?
- Commit phase
	-  If all the services say OK, then it gives order to commit else, it orders for Abort or Rollback

### Issues
1. what if Transaction coordinator fails
2. Participant fails
3. Prepare message / OK message / Abort / Commit message get lost due to above two issues

#### Solution
- Every System has a **log file**
- Prepare msg lost i.e a service didn't get the msg --> participant aborts the transaction / release lock , if after that it receives prepare msg , send back response NO
- If OK message is lost --> TC aborts the transaction
- If commit msg is lost -->blocking period happens, during which the participant thread is blocked , can't do anything else, to resolve this we use 3 Phase commit


## 3 Phase commit (Non Blocking)
1. Prepare phase
2. Pre-commit phase
	1. Whatever decision the Transaction coordinator has taken, it sends to the participants, that in case i go down this is the decision I have taken
3. Commit phase

### What if pre-commit phase fails
- participant asks neighbours has the TC sent you any pre-commit message?
- If not they Abort


## SAGA Pattern
- 2PC and 3PC are Synchronous in nature
- SAGA Pattern is used in a long chain of participants and long transactions

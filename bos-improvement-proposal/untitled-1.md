# 3. Referndum Execution Procedure

### Command Line Quick Start

We use the eosc cmd tool blow. [https://eosc.app/](https://eosc.app/)

Add to your .bashrc or .zshrc file

```text
alias bosc= "eosc -u https://api.boscore.io"
```

### 1. Proposal Submission and Referendum \([eosio.forum](https://github.com/boscore/referendum/tree/master/contracts/eosio.forum)\)

![img](https://uploader.shimo.im/f/K0qO5RiIfVoFNxbU.png!thumbnail)

Proposer proposes proposal

```text
bosc tx create eosio.forum propose '{"proposer": "proposer1", "proposal_name": "example", "title": "The title, for list views", "proposal_json": "", "expires_at": "2019-01-30T17:03:20"}' -p proposer1@active
```

Voter votes proposal

```text
bosc tx create eosio.forum vote '{"voter": "voter1", "proposal_name": "example", "vote": 1, "vote_json": ""}' -p voter1@active
```

Auditor or BPs comment

```text
$ bosc tx create eosio.forum vote '{"voter": "voter1", "proposal_name": "example", "vote": 1, "vote_json": "{\"comment\":\"I vote this newtest proposal\"}"' -p voter1@active
```

### 2. Auditor Nomination and Elections \([auditor.bos](https://github.com/boscore/referendum/tree/master/contracts/auditor.bos)\)

Candidate stakes token

```text
bosc transfer <CANDIDATE> auditor.bos "100.0000 BOS" -m "stake for auditor.bos"
```

Candidate nominates himself/herself

```text
bosc tx create auditor.bos nominatecand '{"cand": "<CANDIDATE>"}' -p <CANDIDATE>@active
```

Voter votes for Auditor Candidate

```text
bosc tx create auditor.bos voteauditor '{"voter":"<VOTER>","newvotes":["<CANDIDATE_1>", "<CANDIDATE_2>","<CANDIDATE_3>"]}' -p deniscarrier
```

### 3. BET/BPs Review and Approve \([escrow.bos](https://github.com/boscore/referendum/tree/master/contracts/escrow.bos)\)

![img](https://uploader.shimo.im/f/0YbGxhOpqG4U5ObT.png)

#### Proposal Approved

**BET Initialize escrow**

```text
bosc tx create escrow.bos init '{"sender":"bet.bos","receiver":"<RECEIVER>","approver":"eosio","escrow_name":"<NAME>","expires_at":"2019-09-15T00:00:00","memo":"BOS escrow"}' -p bet.bos --skip-sign --expiration 36000 --write-transaction init.json
```

Someone propose MSIG proposal

```text
bosc multisig propose <PROPOSER> <PROPOSAL NAME> init.json --request <BET ACCOUNT>,<BET ACCOUNT>...(7 accounts)
```

BET Approve the init escrow \(7 BET MSIG\)

```text
bosc multisig approve <PROPOSER> <PROPOSAL NAME> <BET ACCOUNT>
```

Execute MSIG \(by anyone\)

```text
bosc multisig exec <PROPOSER> <PROSOAL NAME> <EXECUTER> -p <EXECUTER>
```

**BET Transfer Fund**

```text
bosc tx create eosio.token transfer '{"from": "bet.bos", "to":escrow.bos,"quantity":"100.0000 BOS","memo":"init escorw"}' -p bet.bos --skip-sign --expiration 36000 --write-transaction transfer.json
```

Someone propose MSIG proposal

```text
bosc multisig propose <PROPOSER> <PROPOSAL NAME> transfer.json --request <BET ACCOUNT>,<BET ACCOUNT>...(7 accounts)
```

BET Approve the transfer escrow \(7 BET MSIG\)

```text
bosc multisig approve <PROPOSER> <PROPOSAL NAME> <BET ACCOUNT>
```

Execute MSIG \(by anyone\)

```text
bosc multisig exec <PROPOSER> <PROSOAL NAME> <EXECUTER> -p <EXECUTER>
```

**BET Approve escrow \(MSIG\)**

Create a proposal tx json

```text
bosc tx create escrow.bos approve '{"escrow_name": "<NAME>", "approver":"bet.bos"}' -p bet.bos --skip-sign --expiration 36000 --write-transaction approve.json
```

Someone propose MSIG proposal

```text
bosc multisig propose <PROPOSER> <PROPOSAL NAME> approve.json --request <BET ACCOUNT>,<BET ACCOUNT>...(7 accounts)
```

BET Approve the escrow \(7 BET MSIG\)

```text
bosc multisig approve <PROPOSER> <PROPOSAL NAME> <BET ACCOUNT>
```

Execute MSIG \(by anyone\)

```text
bosc multisig exec <PROPOSER> <PROSOAL NAME> <EXECUTER> -p <EXECUTER>
```

**Claim Escrow 100% \(by anyone\)**

```text
bosc tx create escrow.bos claim '{"escrow_name":"<NAME>"}' -p <CLAIMER>
```

#### Review, Approved by BPs, and Claims

**BET Initialize escrow**

```text
bosc tx create escrow.bos init '{"sender":"bet.bos","receiver":"<RECEIVER>","approver":"eosio","escrow_name":"<NAME>","expires_at":"2019-09-15T00:00:00","memo":"BOS escrow"}' -p bet.bos --skip-sign --expiration 36000 --write-transaction init.json
```

Someone propose MSIG proposal

```text
bosc multisig propose <PROPOSER> <PROPOSAL NAME> init.json --request <BET ACCOUNT>,<BET ACCOUNT>...(7 accounts)
```

BET Approve the init escrow \(7 BET MSIG\)

```text
bosc multisig approve <PROPOSER> <PROPOSAL NAME> <BET ACCOUNT>
```

Execute MSIG \(by anyone\)

```text
bosc multisig exec <PROPOSER> <PROSOAL NAME> <EXECUTER> -p <EXECUTER>
```

**BET Transfer Fund**

```text
bosc tx create eosio.token transfer '{"from": "bet.bos", "to":escrow.bos,"quantity":"100.0000 BOS","memo":"init escorw"}' -p bet.bos --skip-sign --expiration 36000 --write-transaction transfer.json
```

Someone propose MSIG proposal

```text
bosc multisig propose <PROPOSER> <PROPOSAL NAME> transfer.json --request <BET ACCOUNT>,<BET ACCOUNT>...(7 accounts)
```

BET Approve the transfer escrow \(7 BET MSIG\)

```text
bosc multisig approve <PROPOSER> <PROPOSAL NAME> <BET ACCOUNT>
```

Execute MSIG \(by anyone\)

```text
bosc multisig exec <PROPOSER> <PROSOAL NAME> <EXECUTER> -p <EXECUTER>
```

**BET disapprove and request BPs review**

```text
bosc tx create escrow.bos review '{"escrow_name":<ESCROW NAME>,"user":<USER ACCOUNT>,"reviewer":"eosio","memo": "review escrow"}' -p <USER ACCOUNT>
```

BP Reviewed and pass the Proposal Create a proposal tx json

```text
bosc tx create escrow.bos approve '{"escrow_name": "<NAME>", "approver":"eosio"}' -p eosio --skip-sign --expiration 36000 --write-transaction review.json
```

Some one post the MSIG Proposal \(request top 30 bps\)

```text
bosc multisig propose <PROPOSER> <PROPOSAL NAME> review.json --request-producers
```

BP Approve the escrow \(MSIG\)

```text
bosc tx create escrow.bos approve '{"escrow_name":"<NAME>","approver":"eosio"}' -p <BP ACCOUNT>
```

Execute MSIG \(by anyone\)

```text
bosc multisig exec <PROPOSER> <PROSOAL NAME> <EXECUTER> -p <EXECUTER>
```

**BET Claim 90% of Fund \(for proposer\), only if the approver account is eosio**

```text
bosc tx create escrow.bos claim '{"escrow_name":"<NAME>"}' -p <ACCOUNT>
```

**BET manually Transfer 10% of fund from the escrow to each BPs and auditors \(for BET\), only if the approver account is eosio**

BET Approve the init escrow \(7 BET MSIG\)

```text
bosc tx create eosio.token transfer '{"from": "escrow.bos", "to":<ACCOUNT>,"quantity":"0.1000 BOS","memo":"Thanks for your opinions"}' -p bet.bos --skip-sign --expiration 36000 --write-transaction approve.json
```

Someone propose MSIG proposal

```text
bosc multisig propose <PROPOSER> <PROPOSAL NAME> transfer.json --request <BET ACCOUNT>,<BET ACCOUNT>...(7 accounts)
```

BET Approve the init escrow \(7 BET MSIG\)

```text
bosc multisig approve <PROPOSER> <PROPOSAL NAME> <BET ACCOUNT>
```

Execute MSIG \(by anyone\)

```text
bosc multisig exec <PROPOSER> <PROSOAL NAME> <EXECUTER> -p <EXECUTER>
```


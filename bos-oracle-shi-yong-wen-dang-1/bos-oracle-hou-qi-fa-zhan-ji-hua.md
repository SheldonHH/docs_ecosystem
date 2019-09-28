# BOS Oracle后期发展计划

### 1.2 风控

风控用户解决提供者和使用者**信息不对称问题**

oracle提供**法庭**，给一个公正决策

让服务提供者损失大于收益，但惩罚需要滞后性

首个服务提供者注册之后可以设置：

1. 设置费用、包括单次、按月、费用类型、价格；
2. 设置订阅费用，订阅以后需要预付费，单条、m多条的费用（同一条数据推给多个订阅）
3. withdraw deposit 

注意：

* 同一个服务器，第二个注册的用户不少于第一个用户抵押的token。
* 服务注册之后，若第一个人设置最低三个人提供数据，当数据提供者达到3个用户的时候，用户才能够获取数据
* 如果第一个人初始化的时候，设置的最低提供这人数为2，那么至少要有两个用户注册这个服务并提供数据，这个服务才可以提供外部使用。

服务的价格格式验证，接受方式，确定性的数据类型，不确定的类型需要注意i一下。五个使用者，抵押命令需要直接扣除，action的时候 transfer可以直接抵押，第一个注册抵押一万，后一个至少一晚，数据持续时间，多长时间推送一次，超过的时间就无效，服务注册以后，最低需要3个数据提供者有3个，3个以上的数据才有效，达不到就没消

### 2.3 注销

数据提供者不想提供数据的时候，可以选择注销。用户注销后，不能再上传数据，也不能获得之后的收益，但是注销后，用户依旧可以领取之前未领取的收益。

执行命令：

```text

```

临时注销：

用户注销后，数据还存在，但是无法上传数据，服务被申诉后，无法收到申诉通知（临时注销暂时不提供服务，资金会冻结，用户表状态status变成2，冻结了不能解抵押，比如有3个人提供数据，其中一个人冻结了，整个服务不可以用）

### 2.4 领取收入

数据提供者提供了数据之后，有人使用，便可以获得奖励，可以采用下面的命令领取。奖励每隔24小时才可以领取一次。

```text
cleos push action ${contract_oracle} claimreward '{"service_id":"0","claim_account":"'${consumer1111}'"}' -p ${consumer1111}@active
```

数据使用者

BOS提供Oracle功能，有用户想要获取链外的数据，可以通过Oracle合约中的服务，Oracle中有人注册响应的服务并提供数据，用户即可以获取到自己想要的该服务的数据。

数据使用者使用数据有两种方式，包月和单次。如果用户想以包月方式获取数据，需要使用订阅命令；如果用户想只获取一次数据，直接执行requestdata。但是在使用之前需要给自己的账户进行充值，充值后，会根据操作进行不同的扣费方式。

### 3.1 充值

充值的方式通过cleos的转账进行，在转账的时候通过memo备注，memo的格式："1,服务id"

例如：

```text
 cleos transfer ocdappuser11  ${contract_oracle} "0.0001 BOS" "1,1"
```

### 3.2 订阅服务

订阅命令：

```text
cleos push action ${contract_oracle} subscribe   '{"service_id":"0","contract_account":"'${contract_consumer}'","action_name":"receivejson", "publickey":"","account":"'${consumer1111}'","amount":"10.0000 BOS", "memo":"test"}' -p ${consumer1111}@active
```

### 3.3 获取数据

用户通过命令单次获取单次收费

```text
cleos push action ${contract_oracle} requestdata '{service_id":0,  "contract_account":"'${contract_consumer}'","action_name":"receivejson","requester":"'${consumer1111}'", "request_content":"eth usd"}' -p ${consumer1111}@active
```

注册仲裁员

只有数据的提供者和使用者才可以注册仲裁员。仲裁员分为全职仲裁员和大众仲裁员，用户在注册仲裁员的时候可以自己选择注册全职仲裁员还是大众仲裁员。主要区别是：1）注册全职仲裁员时抵押的token比大众仲裁员抵押的token多。2）走仲裁流程时，仲裁员的裁决过程。




## P2P 借贷系统设计


#管理员：管理所有的权限

#设置权限

* 1. setBank(address, name) 认证银行
* 2. setP2P(address, name)  认证P2P借贷公司

#角色： 

* 银行：
* P2P借贷公司
* 个人 或 公司

#银行的接口

sendCNY(address, amount)
发行人民币，监管资金的用途（一个银行）。

#P2P借贷公司的接口

* 1. 负责审核用户资料
approveAccount(address)  对用户做实名认证

* 2. 负责审核借贷是否合法
approveCoin(id) 对债券做审核

# 借方（有闲钱的人）

* register(name, id, note)  去P2P公司注册资料，实名认证，数据只存hash，用于验证。反正隐私泄漏。
* check(name, id, note)     检查某个用户资料是否正确
* getCNY(amount)  把钱存到银行，获取比特人民币的代币. 
* purchase(bytes32 name, uint value) 认购某个债券

#贷方（要借钱的人）

去P2P公司注册资料，实名认证
把东西抵押给P2P公司
发行债券
借方 认购债券，借方把比特人民币给贷方。
贷方拿着比特人民币去银行换成资金，用户生产活动。

需要下面的页面：

页面 1 ： 帐户：

1. 注册 + 检查 
2. 个人帐户中心，个人帐户的信息，个人发行的债券，个人购买的债券 ，债券到期了，申请让贷方兑现。
3. 管理员，审核

页面2 ：银行

1. 每个人可以申请领取1000元测试比特人民币。
2. 管理后台检查到这个申请，发送1000比特人民币给对方。

页面3 ： 债券

债券列表 ＋ 认购 ＋ 添加债券

页面4:   交易

只能卖出债券，买入债券直接从订单列表中买入。类似集市。


P2P 小额贷款 区块链实现：

现在P2P小额贷款公司存在的问题：

1. 经手资金，内部猫腻多。存在圈钱跑路的风险。

2. 数据不公开透明，存在篡改风险。
一旦跑路还可能销毁数据库，使得证据缺失。

3. 流动性差，购买的债券只等等待到期兑现，
没有一个市场进行转让

区块链版本可以很好的解决上面的三个问题：

1. P2P公司不经手用户资金，用户资金完全和银行对接，和P2P公司无关。而且，用户资金冲入银行后，换成的比特人民币可以投资多家P2P公司。

2. 数据完全公开透明，P2P公司主要负责牵线搭桥，审核用户资料，无法凭空产生数据，也无法修改数据。

3. 有一个统一的债券转让市场，急用钱的时候可以在这里抛售转让。


# rbitcoin
a rust client for bitcoin

## 1,什么是bitcoin?
一个点对点的电子货币系统。
## 2，电子货币是什么？
电子货币是一种储存在计算机中，可以随网络流通的货币。是纸币的替代品。
## 3，那么如何实现电子货币？
计算机可以储存数据，但是计算机的数据容易被修改。如果让数据不容易被修改，那么就等同于制作一个现实世界的账本了。账本可以记录任何东西，包括数字。如果一种数字(btc,erc20)被大家认可是存在价值，可以记录在账本中，那么就可以作为货币来用。
## 4，如何让数据不容易被修改？
   ### 4.1 在计算机领域，数据可以不容被修改吗？
    不可能，做不到。单独设计硬件也许可以。
   ### 4.2，那么退求其次，计算机可以检测数据是否被修改过吗？
     这是可以的，在计算机领域，我们很容易想到hash函数。
   所以我们可以通过hash函数，检测出被修改的数据。将这些别修改的数据剔除（或者不承认），那么就是不可以篡改的数据。

## 5，以上只是是个人可以相信的账本，价值不大。那么如何可以让所有人相信呢 ？
    所有人都持有一份个人可以相信的账本，那么所有人就相信这个账本了。

## 6，从技术上如何实现，账本如何传输？
    ### 1，账本通过网络传输。

## 7，至此已经实现了一个所有人都可信的账本记录，但是无法增加记录，那么如何增加记录，也就是如何记账？
    ### 1，记录从何而来？
        所有人可以写记录，并提交到bitcoin网络中。
    ### 2，记录如何确定有效？
        通过规则验证，即为有效。
    ### 3，谁有资格记账，如何确定谁来记账？
        所有人都有资格记账。所有人通过一个公平合理的规则选出的人来记账。

## 8，记账的人我们确定了，我们把记账的群体称为矿工，那么如何矿工如何同步记录，并且更新记录？
    ### 1，如果每次记录更新，都传输整个账本，并且记录上hash，会出现什么状态？
        网络不支持，数据越来越大，网络迟早崩溃。账本无法同步。
    ### 2，退求其次，不传输整个账本了？
        只传输更新了的数据。这样缩减了大量的数据，降低了网络的压力。同时带来了新的问题，增加了网络的复杂性。
    ### 3，如果只传输更新的一条记录，那么存在的问题是什么？
        #### 1，计算机资源浪费，一条记录就要计算一条hash。
        #### 2，全网账本不统一，出现大量分叉。

    ### 4，那么传输特定数量的记录就是一个折中方案，这个数量是多少呢？
        我们把这个特定数量的记录称为区块。而这个区块的大小被限定为1M。
  
## 9，记录如何更新解决了，那么新的的出现了，我们用了区块这个概念，那么整个账本如何确定不可篡改呢？
    这个非常容易，从第一个块开始，每个块记录前一个块hash。只要验证所有的hash,并且就可以知道账本的真实性，那么账本就是不可篡改的。我们称这种结构为区块链。

## 10，区块的大小被限定为1M,每次都需要满足1M的记录，才能被记录到账本上，是否合理，如果不合理，如何解决？
    不合理，我发起一笔转账，我不知道我需要等多久，状态才可以被确定。效率太低，并且不方便。
    所有需要限定一个时间，时间到了，区块必须生成，而不是满足1M的区块大小来。
    在bitcoin中，这个时间是10分钟。

## 11，如何选择这个更新区块的人，并且如何防止作恶？
    1，一个公平的游戏规则。
    2，为了防止作恶，就需要需要付出成本，同时获取到系统的奖励，激励记账。
    所以bitcoin，就通过计算hash，来确定记账权利。
        第一个计算出特定hash的，即拥有记账权利。计算hash，需要付出算力成本。
    4，为什么这么设定记账规则？
        确保公平，确保所有人都可以相信这个账本，而不只是少数人可以篡改，并且只有少数人可以相信。

## 12, 到目前为止，只需要设定合理的记账规则，那么这个系统就是合理的？
    只要记账规则合理，就不会存在双花之类的问题。这些都是记账层面的问题，而不是整个bitcoin 系统的问题。



## 记录的设计（转账）。
    1，如何确定个人身份，在计算机中？
        计算机签名。密码学。非对称加密体系。

    2， utxo。这个其实是不必要的？
        存在的作用，可以用来验证交易有效。防止了签名重复有效。同时引入了脚本系统，扩大了bitcoin的可扩展性和适用性。

        



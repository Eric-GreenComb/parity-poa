# parity-poa-tutorial

A complete set of files produced in the Parity PoA chain tutorial.

## 创建网络

- 创建节点node0

parity --config node00.toml

- 创建用户(fifu0,eric)

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["fifu0", "fifu0"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8540

return : 0x008b7b778ae54d339df2455a554be8ab46e7553c

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["eric", "eric"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8540

return : 0x00eaf5c65f32917c922364e4892b5ec5a35baa6e

- 创建节点node1

parity --config node11.toml

- 创建用户(fifu1)

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["fifu1", "fifu1"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8541

return : 0x00073e4af6ff4b69819168204d992f489d86139f

parity --config node0.toml

parity --config node1.toml

parity --config node2.toml

parity --config node3.toml

## 链接网络

- 查看node0

curl --data '{"jsonrpc":"2.0","method":"parity_enode","params":[],"id":0}' -H "Content-Type: application/json" -X POST localhost:8540

- 链接

curl --data '{"jsonrpc":"2.0","method":"parity_addReservedPeer","params":["enode://51edf5058b0042bd7ab6ab3126b778fb1822ea1000fae7582bdcb71d3f4b116e8c603ca48bfe311f66d699001a626db5282c1217d97725a4c97424e8c30a0381@192.168.1.104:30300"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8541

## 创建合约

curl --data '{"jsonrpc":"2.0","method":"parity_addReservedPeer","params":["enode://2fa636df4d8a062c8c86caf20b2b6e37aee29ce175f7fefbe5705e1309d60a3822a18f3011fa7faad8b220e7969cac146e43c6abce83edd18bcf42b73e0c9a4e@10.16.52.97:30300"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8541

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["eric", "eric"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8541

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["alan", "alan"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8541

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["node2", "node2"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8542

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["node3", "node3"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8543

### cmd

parity --rpc --rpccorsdomain "*" --port "30300" --rpcapi "db,eth,net,web3" --unlock '0' --password /home/eric/go/geth/password --nodiscover --maxpeers '50' --networkid '33042' --datadir '/home/eric/go/geth' --ipcpath /home/eric/.ethereum/geth.ipc console

parity --identity "ethTest" --rpc --rpccorsdomain "*" --datadir /home/eric/go/src/github.com/Eric-GreenComb/parity-poa/parity0 --port 30300 --rpcapi "db,eth,net,web3" --networkid '33042' console

### transfer data

data:
0x + a9059cbb + 00000000000000000000000000eaF5c65F32917c922364e4892b5EC5A35baa6E + 00000000000000000000000000000000000000000000021e19e0c9bab2400000

0xa9059cbb00000000000000000000000000eaF5c65F32917c922364e4892b5EC5A35baa6E00000000000000000000000000000000000000000000021e19e0c9bab2400000

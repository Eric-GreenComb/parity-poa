# parity-poa-tutorial

A complete set of files produced in the Parity PoA chain tutorial.

## 创建网络

- 创建节点node0

parity --config node00.toml

- 创建用户(node0,user)

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["node0", "node0"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8540

return : 0x00bd138abd70e2f00903268f3db08f2d25677c9e

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["user", "user"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8540

return : 0x004ec07d2329997267ec62b4166639513386f32e

- 创建节点node1

parity --config node11.toml

- 创建用户(node1)

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["node1", "node1"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8541

return : 0x00aa39d30f0d20ff03a22ccfc30b7efbfca597c2

parity --config node0.toml

parity --config node1.toml

## 链接网络

- 查看node0

curl --data '{"jsonrpc":"2.0","method":"parity_enode","params":[],"id":0}' -H "Content-Type: application/json" -X POST localhost:8540

- 链接

curl --data '{"jsonrpc":"2.0","method":"parity_addReservedPeer","params":["enode://507d1385e46e2aadb5fd9b0140b5f990daaa177f68d3a187b7e7bc5ebe7c7158ab9c4b53b2d098495489c03d925a72d5e824dba974c7238ec33d0278ebbebfa3@10.16.71.16:30300"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8541

## 创建合约

curl --data '{"jsonrpc":"2.0","method":"parity_addReservedPeer","params":["enode://2fa636df4d8a062c8c86caf20b2b6e37aee29ce175f7fefbe5705e1309d60a3822a18f3011fa7faad8b220e7969cac146e43c6abce83edd18bcf42b73e0c9a4e@10.16.52.97:30300"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8541

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["eric", "eric"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8541

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["alan", "alan"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8541

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["node2", "node2"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8542

curl --data '{"jsonrpc":"2.0","method":"parity_newAccountFromPhrase","params":["node3", "node3"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8543
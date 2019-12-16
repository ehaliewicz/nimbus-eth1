# Introduction
`wakunode` is a cli application that allows you to run a
[Waku](https://github.com/vacp2p/specs/blob/master/waku.md) enabled node.

The application and Waku specification are still experimental and fully in flux.

Additionally the original Whisper (EIP-627) protocol can also be enabled as can
an experimental Whisper - Waku bridging option.

# How to Build & Run

```bash
make wakunode
./build/wakunode --help
```

# Testing Waku Protocol
One can set up several nodes, get them connected and then instruct them via the
JSON-RPC interface. This can be done via e.g. web3.js, nim-web3 (needs to be
updated) or simply curl your way out.

The JSON-RPC interface is currently the same as the one of Whisper. The only
difference is the addition of broadcasting the topics interest when a filter
with a certain set of topics is subcribed.

Example of a quick test with nim-web3:
```
./build/wakunode --log-level:DEBUG --bootnode-only --nodekey:5dc5381cae54ba3174dc0d46040fe11614d0cc94d41185922585198b4fcef9d3

./build/wakunode --log-level:DEBUG --bootnodes:enode://e5fd642a0f630bbb1e4cd7df629d7b8b019457a9a74f983c0484a045cebb176def86a54185b50bbba6bbf97779173695e92835d63109c23471e6da382f922fdb@0.0.0.0:30303 --rpc --ports-shift:1 --waku-mode:WakuSan

./build/wakunode --log-level:DEBUG --bootnodes:enode://e5fd642a0f630bbb1e4cd7df629d7b8b019457a9a74f983c0484a045cebb176def86a54185b50bbba6bbf97779173695e92835d63109c23471e6da382f922fdb@0.0.0.0:30303 --rpc --ports-shift:2 --waku-mode:WakuChan

./build/quicksim
```
# Raft Block Chain

Inspired by UCSB CS 171 Distributed System's project on the Paxos protocol, which I implemented at https://github.com/nicomwong/paxosBlockChain.

This project is similar, but it implements the Raft protocol for consensus in a distributed system. The Raft protocol is said to be easier to understand and more specifically defined for a multi-consensus application than Paxos. Similar to the aforementioned project, this implementation gaurantees the consistency of a replicated, append-only block chain (log) and key-value store (a simple state machine).

The description of the Raft protocol can be found here: https://raft.github.io/raft.pdf.


# How to Use

First, this implementation assumes a permissioned system, so the user must specify the number of servers. To do this:

* In **server.py**, set `Server.numServers` to the number of desired servers **N**.
* In **client.py**, set `Client.numServers` to **N**.

<br/>

Second, start the servers and clients. Note that each server or client must be run in its own process (e.g. a separate bash process).

* Start the servers by running `$ python3 server.py <serverID>` **N** times with `serverID = 1, 2, 3, ..., N`.
   * For example, if `numServers = 3`, then run `$ python3 server.py 1`, `$ python3 server.py 2`, and `$ python3 server.py 3` on seperate terminals.

* Start the client(s) by running `$ python3 client.py <clientID>` once for each desired client and each with a unique `clientID` in the set `{1, 2, 3, ..., 999}`.
   * For example, if you want 2 clients, you can run `$ python3 client.py 1` and `$ python3 client.py 4` on separate terminals.

<br/>

Third, initiate commands through a client! The available commands are as follows:
* `get <key>` where `key` is a Python literal such as `"a string"`, `'a string'`, `1`, `{'key1':'val1'}`, etc.
* `put <key> <value>` where `key` and `value` are Python literals.

<br/>

Fourth, wait for a query response to be received.
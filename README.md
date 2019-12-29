# bitcoind(1) - manual page for bitcoind v0.19.0.1

Version 0.19.0.1, November 2019

```
bitcoind [options]                     Start Bitcoin Core
```

<a name="description"></a>

# Description

Bitcoin Core version v0.19.0.1

<a name="options"></a>

# Options

.HP
-?

* Print this help message and exit
  .HP
  **-alertnotify=**&lt;cmd&gt;
* Execute command when a relevant alert is received or we see a really
  long fork (%s in cmd is replaced by message)
  .HP
  **-assumevalid=**&lt;hex&gt;
* If this block is in the chain assume that it and its ancestors are valid
  and potentially skip their script verification (0 to verify all,
  default:
  00000000000000000005f8920febd3925f8272a6a71237563d78c2edfdd09ddf,
  testnet:
  00000000000000b7ab6ce61eb6d571003fbe5fe892da4c9b740c49a07542462d)
  .HP
  **-blockfilterindex=**&lt;type&gt;
* Maintain an index of compact filters by block (default: 0, values:
  basic). If &lt;type&gt; is not supplied or if &lt;type&gt; = 1, indexes for
  all known types are enabled.
  .HP
  **-blocknotify=**&lt;cmd&gt;
* Execute command when the best block changes (%s in cmd is replaced by
  block hash)
  .HP
  **-blockreconstructionextratxn=**&lt;n&gt;
* Extra transactions to keep in memory for compact block reconstructions
  (default: 100)
  .HP
  **-blocksdir=**&lt;dir&gt;
* Specify directory to hold blocks subdirectory for *.dat files (default:
  &lt;datadir&gt;)
  .HP
  **-blocksonly**
* Whether to reject transactions from network peers. Transactions from the
  wallet, RPC and relay whitelisted inbound peers are not affected.
  (default: 0)
  .HP
  **-conf=**&lt;file&gt;
* Specify configuration file. Relative paths will be prefixed by datadir
  location. (default: bitcoin.conf)
  .HP
  **-daemon**
* Run in the background as a daemon and accept commands
  .HP
  **-datadir=**&lt;dir&gt;
* Specify data directory
  .HP
  **-dbcache=**&lt;n&gt;
* Maximum database cache size &lt;n&gt; MiB (4 to 16384, default: 450). In
  addition, unused mempool memory is shared for this cache (see
  **-maxmempool**).
  .HP
  **-debuglogfile=**&lt;file&gt;
* Specify location of debug log file. Relative paths will be prefixed by a
  net-specific datadir location. (**-nodebuglogfile** to disable;
  default: debug.log)
  .HP
  **-includeconf=**&lt;file&gt;
* Specify additional configuration file, relative to the **-datadir** path
  (only useable from configuration file, not command line)
  .HP
  **-loadblock=**&lt;file&gt;
* Imports blocks from external blk000??.dat file on startup
  .HP
  **-maxmempool=**&lt;n&gt;
* Keep the transaction memory pool below &lt;n&gt; megabytes (default: 300)
  .HP
  **-maxorphantx=**&lt;n&gt;
* Keep at most &lt;n&gt; unconnectable transactions in memory (default: 100)
  .HP
  **-mempoolexpiry=**&lt;n&gt;
* Do not keep transactions in the mempool longer than &lt;n&gt; hours (default:
  336)
  .HP
  **-par=**&lt;n&gt;
* Set the number of script verification threads (**-6** to 16, 0 = auto, &lt;0 =
  leave that many cores free, default: 0)
  .HP
  **-persistmempool**
* Whether to save the mempool on shutdown and load on restart (default: 1)
  .HP
  **-pid=**&lt;file&gt;
* Specify pid file. Relative paths will be prefixed by a net-specific
  datadir location. (default: bitcoind.pid)
  .HP
  **-prune=**&lt;n&gt;
* Reduce storage requirements by enabling pruning (deleting) of old
  blocks. This allows the pruneblockchain RPC to be called to
  delete specific blocks, and enables automatic pruning of old
  blocks if a target size in MiB is provided. This mode is
  incompatible with **-txindex** and **-rescan**. Warning: Reverting this
  setting requires re-downloading the entire blockchain. (default:
  0 = disable pruning blocks, 1 = allow manual pruning via RPC,
  &gt;=550 = automatically prune block files to stay under the
  specified target size in MiB)
  .HP
  **-reindex**
* Rebuild chain state and block index from the blk*.dat files on disk
  .HP
  **-reindex-chainstate**
* Rebuild chain state from the currently indexed blocks. When in pruning
  mode or if blocks on disk might be corrupted, use full **-reindex**
  instead.
  .HP
  **-sysperms**
* Create new files with system default permissions, instead of umask 077
  (only effective with disabled wallet functionality)
  .HP
  **-txindex**
* Maintain a full transaction index, used by the getrawtransaction rpc
  call (default: 0)
  .HP
  **-version**
* Print version and exit

Connection options:
.HP
**-addnode=**&lt;ip&gt;

* Add a node to connect to and attempt to keep the connection open (see
  the \`addnode\` RPC command help for more info). This option can be
  specified multiple times to add multiple nodes.
  .HP
  **-banscore=**&lt;n&gt;
* Threshold for disconnecting misbehaving peers (default: 100)
  .HP
  **-bantime=**&lt;n&gt;
* Number of seconds to keep misbehaving peers from reconnecting (default:
  86400)
  .HP
  **-bind=**&lt;addr&gt;
* Bind to given address and always listen on it. Use [host]:port notation
  for IPv6
  .HP
  **-connect=**&lt;ip&gt;
* Connect only to the specified node; **-noconnect** disables automatic
  connections (the rules for this peer are the same as for
  **-addnode**). This option can be specified multiple times to connect
  to multiple nodes.
  .HP
  **-discover**
* Discover own IP addresses (default: 1 when listening and no **-externalip**
  or **-proxy**)
  .HP
  **-dns**
* Allow DNS lookups for **-addnode**, **-seednode** and **-connect** (default: 1)
  .HP
  **-dnsseed**
* Query for peer addresses via DNS lookup, if low on addresses (default: 1
  unless **-connect** used)
  .HP
  **-enablebip61**
* Send reject messages per BIP61 (default: 0)
  .HP
  **-externalip=**&lt;ip&gt;
* Specify your own public address
  .HP
  **-forcednsseed**
* Always query for peer addresses via DNS lookup (default: 0)
  .HP
  **-listen**
* Accept connections from outside (default: 1 if no **-proxy** or **-connect**)
  .HP
  **-listenonion**
* Automatically create Tor hidden service (default: 1)
  .HP
  **-maxconnections=**&lt;n&gt;
* Maintain at most &lt;n&gt; connections to peers (default: 125)
  .HP
  **-maxreceivebuffer=**&lt;n&gt;
* Maximum per-connection receive buffer, &lt;n&gt;*1000 bytes (default: 5000)
  .HP
  **-maxsendbuffer=**&lt;n&gt;
* Maximum per-connection send buffer, &lt;n&gt;*1000 bytes (default: 1000)
  .HP
  **-maxtimeadjustment**
* Maximum allowed median peer time offset adjustment. Local perspective of
  time may be influenced by peers forward or backward by this
  amount. (default: 4200 seconds)
  .HP
  **-maxuploadtarget=**&lt;n&gt;
* Tries to keep outbound traffic under the given target (in MiB per 24h),
  0 = no limit (default: 0)
  .HP
  **-onion=**&lt;ip:port&gt;
* Use separate SOCKS5 proxy to reach peers via Tor hidden services, set
  **-noonion** to disable (default: **-proxy**)
  .HP
  **-onlynet=**&lt;net&gt;
* Make outgoing connections only through network &lt;net&gt; (ipv4, ipv6 or
  onion). Incoming connections are not affected by this option.
  This option can be specified multiple times to allow multiple
  networks.
  .HP
  **-peerbloomfilters**
* Support filtering of blocks and transaction with bloom filters (default:
  0)
  .HP
  **-permitbaremultisig**
* Relay non-P2SH multisig (default: 1)
  .HP
  **-port=**&lt;port&gt;
* Listen for connections on &lt;port&gt; (default: 8333, testnet: 18333,
  regtest: 18444)
  .HP
  **-proxy=**&lt;ip:port&gt;
* Connect through SOCKS5 proxy, set **-noproxy** to disable (default:
  disabled)
  .HP
  **-proxyrandomize**
* Randomize credentials for every proxy connection. This enables Tor
  stream isolation (default: 1)
  .HP
  **-seednode=**&lt;ip&gt;
* Connect to a node to retrieve peer addresses, and disconnect. This
  option can be specified multiple times to connect to multiple
  nodes.
  .HP
  **-timeout=**&lt;n&gt;
* Specify connection timeout in milliseconds (minimum: 1, default: 5000)
  .HP
  **-torcontrol=**&lt;ip&gt;:&lt;port&gt;
* Tor control port to use if onion listening enabled (default:
  127.0.0.1:9051)
  .HP
  **-torpassword=**&lt;pass&gt;
* Tor control port password (default: empty)
  .HP
  **-upnp**
* Use UPnP to map the listening port (default: 0)
  .HP
  **-whitebind=**&lt;[permissions@]addr&gt;
* Bind to given address and whitelist peers connecting to it. Use
  [host]:port notation for IPv6. Allowed permissions are
  bloomfilter (allow requesting BIP37 filtered blocks and
  transactions), noban (do not ban for misbehavior), forcerelay
  (relay even non-standard transactions), relay (relay even in
  **-blocksonly** mode), and mempool (allow requesting BIP35 mempool
  contents). Specify multiple permissions separated by commas
  (default: noban,mempool,relay). Can be specified multiple times.
  .HP
  **-whitelist=**&lt;[permissions@]IP address or network&gt;
* Whitelist peers connecting from the given IP address (e.g. 1.2.3.4) or
  CIDR notated network(e.g. 1.2.3.0/24). Uses same permissions as
  **-whitebind**. Can be specified multiple times.

Wallet options:
.HP
**-addresstype**

* What type of addresses to use ("legacy", "p2sh-segwit", or "bech32",
  default: "p2sh-segwit")
  .HP
  **-avoidpartialspends**
* Group outputs by address, selecting all or none, instead of selecting on
  a per-output basis. Privacy is improved as an address is only
  used once (unless someone sends to it after spending from it),
  but may result in slightly higher fees as suboptimal coin
  selection may result due to the added limitation (default: 0
  (always enabled for wallets with "avoid_reuse" enabled))
  .HP
  **-changetype**
* What type of change to use ("legacy", "p2sh-segwit", or "bech32").
  Default is same as **-addresstype**, except when
  **-addresstype**=_p2sh-segwit_ a native segwit output is used when
  sending to a native segwit address)
  .HP
  **-disablewallet**
* Do not load the wallet and disable wallet RPC calls
  .HP
  **-discardfee=**&lt;amt&gt;
* The fee rate (in BTC/kB) that indicates your tolerance for discarding
  change by adding it to the fee (default: 0.0001). Note: An output
  is discarded if it is dust at this rate, but we will always
  discard up to the dust relay fee and a discard fee above that is
  limited by the fee estimate for the longest target
  .HP
  **-fallbackfee=**&lt;amt&gt;
* A fee rate (in BTC/kB) that will be used when fee estimation has
  insufficient data (default: 0.0002)
  .HP
  **-keypool=**&lt;n&gt;
* Set key pool size to &lt;n&gt; (default: 1000)
  .HP
  **-mintxfee=**&lt;amt&gt;
* Fees (in BTC/kB) smaller than this are considered zero fee for
  transaction creation (default: 0.00001)
  .HP
  **-paytxfee=**&lt;amt&gt;
* Fee (in BTC/kB) to add to transactions you send (default: 0.00)
  .HP
  **-rescan**
* Rescan the block chain for missing wallet transactions on startup
  .HP
  **-salvagewallet**
* Attempt to recover private keys from a corrupt wallet on startup
  .HP
  **-spendzeroconfchange**
* Spend unconfirmed change when sending transactions (default: 1)
  .HP
  **-txconfirmtarget=**&lt;n&gt;
* If paytxfee is not set, include enough fee so transactions begin
  confirmation on average within n blocks (default: 6)
  .HP
  **-upgradewallet**
* Upgrade wallet to latest format on startup
  .HP
  **-wallet=**&lt;path&gt;
* Specify wallet database path. Can be specified multiple times to load
  multiple wallets. Path is interpreted relative to &lt;walletdir&gt; if
  it is not absolute, and will be created if it does not exist (as
  a directory containing a wallet.dat file and log files). For
  backwards compatibility this will also accept names of existing
  data files in &lt;walletdir&gt;.)
  .HP
  **-walletbroadcast**
* Make the wallet broadcast transactions (default: 1)
  .HP
  **-walletdir=**&lt;dir&gt;
* Specify directory to hold wallets (default: &lt;datadir&gt;/wallets if it
  exists, otherwise &lt;datadir&gt;)
  .HP
  **-walletnotify=**&lt;cmd&gt;
* Execute command when a wallet transaction changes (%s in cmd is replaced
  by TxID)
  .HP
  **-walletrbf**
* Send transactions with full-RBF opt-in enabled (RPC only, default: 0)
  .HP
  **-zapwallettxes=**&lt;mode&gt;
* Delete all wallet transactions and only recover those parts of the
  blockchain through **-rescan** on startup (1 = keep tx meta data e.g.
  payment request information, 2 = drop tx meta data)

ZeroMQ notification options:
.HP
**-zmqpubhashblock=**&lt;address&gt;

* Enable publish hash block in &lt;address&gt;
  .HP
  **-zmqpubhashblockhwm=**&lt;n&gt;
* Set publish hash block outbound message high water mark (default: 1000)
  .HP
  **-zmqpubhashtx=**&lt;address&gt;
* Enable publish hash transaction in &lt;address&gt;
  .HP
  **-zmqpubhashtxhwm=**&lt;n&gt;
* Set publish hash transaction outbound message high water mark (default:
  1000)
  .HP
  **-zmqpubrawblock=**&lt;address&gt;
* Enable publish raw block in &lt;address&gt;
  .HP
  **-zmqpubrawblockhwm=**&lt;n&gt;
* Set publish raw block outbound message high water mark (default: 1000)
  .HP
  **-zmqpubrawtx=**&lt;address&gt;
* Enable publish raw transaction in &lt;address&gt;
  .HP
  **-zmqpubrawtxhwm=**&lt;n&gt;
* Set publish raw transaction outbound message high water mark (default:
  1000)

Debugging/Testing options:
.HP
**-debug=**&lt;category&gt;

* Output debugging information (default: **-nodebug**, supplying &lt;category&gt; is
  optional). If &lt;category&gt; is not supplied or if &lt;category&gt; = 1,
  output all debugging information. &lt;category&gt; can be: net, tor,
  mempool, http, bench, zmq, db, rpc, estimatefee, addrman,
  selectcoins, reindex, cmpctblock, rand, prune, proxy, mempoolrej,
  libevent, coindb, qt, leveldb.
  .HP
  **-debugexclude=**&lt;category&gt;
* Exclude debugging information for a category. Can be used in conjunction
  with **-debug**=_1_ to output debug logs for all categories except one
  or more specified categories.
  .HP
  **-help-debug**
* Print help message with debugging options and exit
  .HP
  **-logips**
* Include IP addresses in debug output (default: 0)
  .HP
  **-logthreadnames**
* Prepend debug output with name of the originating thread (only available
  on platforms supporting thread_local) (default: 0)
  .HP
  **-logtimestamps**
* Prepend debug output with timestamp (default: 1)
  .HP
  **-maxtxfee=**&lt;amt&gt;
* Maximum total fees (in BTC) to use in a single wallet transaction;
  setting this too low may abort large transactions (default: 0.10)
  .HP
  **-printtoconsole**
* Send trace/debug info to console (default: 1 when no **-daemon**. To disable
  logging to file, set **-nodebuglogfile**)
  .HP
  **-shrinkdebugfile**
* Shrink debug.log file on client startup (default: 1 when no **-debug**)
  .HP
  **-uacomment=**&lt;cmt&gt;
* Append comment to the user agent string

Chain selection options:
.HP
**-chain=**&lt;chain&gt;

* Use the chain &lt;chain&gt; (default: main). Allowed values: main, test,
  regtest
  .HP
  **-testnet**
* Use the test chain. Equivalent to **-chain**=_test_.

Node relay options:
.HP
**-bytespersigop**

* Equivalent bytes per sigop in transactions for relay and mining
  (default: 20)
  .HP
  **-datacarrier**
* Relay and mine data carrier transactions (default: 1)
  .HP
  **-datacarriersize**
* Maximum size of data in data carrier transactions we relay and mine
  (default: 83)
  .HP
  **-minrelaytxfee=**&lt;amt&gt;
* Fees (in BTC/kB) smaller than this are considered zero fee for relaying,
  mining and transaction creation (default: 0.00001)
  .HP
  **-whitelistforcerelay**
* Add 'forcerelay' permission to whitelisted inbound peers with default
  permissions. This will relay transactions even if the
  transactions were already in the mempool or violate local relay
  policy. (default: 0)
  .HP
  **-whitelistrelay**
* Add 'relay' permission to whitelisted inbound peers with default
  permissions. The will accept relayed transactions even when not
  relaying transactions (default: 1)

Block creation options:
.HP
**-blockmaxweight=**&lt;n&gt;

* Set maximum BIP141 block weight (default: 3996000)
  .HP
  **-blockmintxfee=**&lt;amt&gt;
* Set lowest fee rate (in BTC/kB) for transactions to be included in block
  creation. (default: 0.00001)

RPC server options:
.HP
**-rest**

* Accept public REST requests (default: 0)
  .HP
  **-rpcallowip=**&lt;ip&gt;
* Allow JSON-RPC connections from specified source. Valid for &lt;ip&gt; are a
  single IP (e.g. 1.2.3.4), a network/netmask (e.g.
  1.2.3.4/255.255.255.0) or a network/CIDR (e.g. 1.2.3.4/24). This
  option can be specified multiple times
  .HP
  **-rpcauth=**&lt;userpw&gt;
* Username and HMAC-SHA-256 hashed password for JSON-RPC connections. The
  field &lt;userpw&gt; comes in the format: &lt;USERNAME&gt;:&lt;SALT&gt;$&lt;HASH&gt;. A
  canonical python script is included in share/rpcauth. The client
  then connects normally using the
  rpcuser=&lt;USERNAME&gt;/rpcpassword=&lt;PASSWORD&gt; pair of arguments. This
  option can be specified multiple times
  .HP
  **-rpcbind=**&lt;addr&gt;[:port]
* Bind to given address to listen for JSON-RPC connections. Do not expose
  the RPC server to untrusted networks such as the public internet!
  This option is ignored unless **-rpcallowip** is also passed. Port is
  optional and overrides **-rpcport**. Use [host]:port notation for
  IPv6. This option can be specified multiple times (default:
  127.0.0.1 and ::1 i.e., localhost)
  .HP
  **-rpccookiefile=**&lt;loc&gt;
* Location of the auth cookie. Relative paths will be prefixed by a
  net-specific datadir location. (default: data dir)
  .HP
  **-rpcpassword=**&lt;pw&gt;
* Password for JSON-RPC connections
  .HP
  **-rpcport=**&lt;port&gt;
* Listen for JSON-RPC connections on &lt;port&gt; (default: 8332, testnet:
  18332, regtest: 18443)
  .HP
  **-rpcserialversion**
* Sets the serialization of raw transaction or block hex returned in
  non-verbose mode, non-segwit(0) or segwit(1) (default: 1)
  .HP
  **-rpcthreads=**&lt;n&gt;
* Set the number of threads to service RPC calls (default: 4)
  .HP
  **-rpcuser=**&lt;user&gt;
* Username for JSON-RPC connections
  .HP
  **-server**
* Accept command line and JSON-RPC commands

<a name="copyright"></a>

# Copyright

Copyright (C) 2009-2019 The Bitcoin Core developers

Please contribute if you find Bitcoin Core useful. Visit
&lt;https://bitcoincore.org&gt; for further information about the software.
The source code is available from &lt;https://github.com/bitcoin/bitcoin&gt;.

This is experimental software.
Distributed under the MIT software license, see the accompanying file COPYING
or &lt;https://opensource.org/licenses/MIT&gt;

This product includes software developed by the OpenSSL Project for use in the
OpenSSL Toolkit &lt;https://www.openssl.org&gt; and cryptographic software written by
Eric Young and UPnP software written by Thomas Bernard.

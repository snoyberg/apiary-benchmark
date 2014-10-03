benchmark
===
benchmark result of haskell lightweight web frameworks.

libraries
---
* apiary
* scotty
* Spock

how to run
---
```.sh
cabal update
cabal sandbox init
cabal get apiary-0.18.0 Spock-0.7.0.0 scotty-0.9.0
cabal install ./apiary-0.18.0 ./Spock-0.7.0.0 ./scotty-0.9.0
./scripts/all.sh apiary-0.18.0 Spock-0.7.0.0 scotty-0.9.0
```

benchmarks
---
1. HELLO (no capture)
2. PARAM (capture route parameter)
3. DEEP  (deep and many routes)
3. AFTER_DEEP (after DEEP route)

machines
---

### server1

```.sh
% uname -a
Linux server1 3.2.0-4-amd64 #1 SMP Debian 3.2.57-3+deb7u2 x86_64 GNU/Linux
% cat /proc/cpuinfo | grep 'model name'
model name	: Intel(R) Core(TM) i3-2120T CPU @ 2.60GHz
model name	: Intel(R) Core(TM) i3-2120T CPU @ 2.60GHz
model name	: Intel(R) Core(TM) i3-2120T CPU @ 2.60GHz
model name	: Intel(R) Core(TM) i3-2120T CPU @ 2.60GHz
% cat /proc/meminfo | grep MemTotal
MemTotal:       16354960 kB
```

results
---

### single thread

![result](./results/1/result-server1.png)

|machine  |ghc    |framework    |HELLO   |PARAM   |DEEP    |AFTER_DEEP|
|---------|-------|-------------|--------|--------|--------|----------|
|server1  |7.8.3  |apiary-0.18.0|35142.22|28986.17|32288.07|37477.12  |
|server1  |7.8.3  |Spock-0.7.0.0|27513.48|24213.93|29660.93|28646.52  |
|server1  |7.8.3  |scotty-0.9.0 |28354.12|16341.25|2597.80 |9322.60   |

references
---
1. [agrafix/Spock-scotty-benchmark](https://github.com/agrafix/Spock-scotty-benchmark)

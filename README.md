
    -a, --algo                     Specify the hash algorithm to use.
                                   astralhash
                                   balloon
                                   bcd
                                   bitcore
                                   c11
                                   dedal
                                   etchash
                                   ethash
                                   geek
                                   hmq1725
                                   honeycomb
                                   jeonghash
                                   kawpow
                                   lyra2z
                                   megabtx
                                   megamec
                                   mtp
                                   mtp-tcr
                                   multi
                                   octopus
                                   padihash
                                   pawelhash
                                   phi
                                   polytimos
                                   progpow
                                   progpow-veil
                                   progpow-veriblock
                                   progpowz
                                   sha256q
                                   sha256t
                                   skunk
                                   sonoa
                                   tensority
                                   timetravel
                                   tribus
                                   x11r
                                   x16r
                                   x16rt
                                   x16rv2
                                   x16s
                                   x17
                                   x21s
                                   x22i
                                   x25x
                                   x33
        --coin                     [Ethash, ProgPOW] Set coin name.
                                   Helps avoid DAG rebuilds when switching back from a dev fee session.
                                   Example: "eth" for Ethereum, "zil" for Zilliqa.
        --extra-dag-epoch          Allocate extra DAG at GPU for specified epoch. Can be useful for dual mining
                                   of coins like Zilliqa (ZIL). (eg: --extra-dag-epoch 0)
        --nonce-start              [Ethash, ProgPOW] Starting nonce for the solution search.
        --nonce-range-size         [Ethash, ProgPOW] Nonce range size for nonce search. The range will be split between all devices.
    -d, --devices                  Comma separated list of CUDA devices to use.
                                   Device IDs start counting from 0.
        --pci-indexing             Sort devices by PCI bus ID. Device IDs start with 0.
        --ab-indexing              Afterburner indexing (same as --pci-indexing but starts from 1).
    -i, --intensity                GPU intensity 8-25 (default: auto).
        --low-load                 Low load mode (default: 0). 1 - enabled, 0 - disabled.
                                   Reduces the load on the GPUs if possible. Can be set to a comma separated string to enable
                                   the mode for a subset of the GPU list (eg: --low-load 0,0,1,0)
        --kernel                   [Ethash] Choose CUDA kernel (default: 0). Range from 0 to 5.
                                   Set to 0 to enable auto-tuning: the miner will benchmark each kernel and select the fastest.
                                   Can be set to a comma separated list to apply different values to different cards.
                                   (eg: --kernel 2,1,1,3)
                                   The support for this parameter may later be extended to cover other algorithms.
        --gpu-init-mode            Enables DAG sequential initialization (default: 0).
                                   0 - all GPUs are initialized in parallel
                                   1 - fully sequential initialization, one GPU at a time
                                   2 - two GPUs at a time
                                   etc.
        --dag-build-mode           [Ethash, ProgPOW, Octopus] Controls how DAG is built (default: 0).
                                   0 - auto (miner will choose the most appropriate mode based on the GPU model)
                                   1 - default (suitable for most graphics cards)
                                   2 - recommended for 30xx cards to prevent invalid shares
                                   Can be set to a comma separated list to apply different values to different cards.
                                   (eg: --dag-build-mode 1,1,2,1)
        --keep-gpu-busy            Continue mining even in case of connection loss.

    -o, --url                      URL of the mining pool in the following format: <scheme>://<host>:<port>
                                   Supported schemes: stratum+tcp
                                                      stratum+ssl
                                                      stratum+http
                                                      stratum2+tcp
                                                      stratum2+ssl
                                   stratum2 is normally used by Nicehash, MiningPoolHub and other similar mining pools
                                   Example: stratum+tcp://eu1.ethermine.org:4444
                                            stratum+ssl://zcoin.mintpond.com:3005
                                            stratum2+tcp://daggerhashimoto.hk.nicehash.com:3353
    -u, --user                     Username for mining server.
    -p, --pass                     Password for mining server.
    -w, --worker                   Worker name.

    -r, --retries                  Number of times to retry if a network call fails.
    -R, --retry-pause              Pause in seconds between retries.
    -T, --timeout                  Network timeout, in seconds (default: 300)
        --time-limit               Miner shutdown interval in seconds. (default: 0 - disabled)

        --temperature-color        Set temperature color for GPUs stat. Example: 55,65 - it means that
                                   temperatures above 55 will have yellow color, above 65 - red color. (default: 67,77)
        --temperature-limit        GPU shutdown temperature. (default: 0 - disabled)
        --temperature-start        GPU temperature to enable card after disable. (default: 0 - disabled)

    -b, --api-bind-telnet          IP:port for the miner API via telnet (default: 127.0.0.1:4068). Set to 0 to disable.
                                   For external access set IP to 0.0.0.0, in which case setting "--api-read-only" is
                                   recommended as well.
        --api-bind-http            IP:port for the miner API via HTTP (default: 127.0.0.1:4067). Set to 0 to disable.
                                   For external access set IP to 0.0.0.0, in which case setting "--api-read-only" is
                                   recommended as well.
        --api-read-only            Allow only read operations for API calls.
    -J  --json-response            Telnet API server will make json responses.

    -N, --hashrate-avr             Sliding window length in seconds used to compute average hashrate (default: 60).
        --sharerate-avr            Sliding window length in seconds used to compute sharerate (default: 600).
        --gpu-report-interval      GPU stats report frequency. Minimum is 5 sec. (default: 30 sec)
        --gpu-report-interval-s    GPU stats report frequency in shares. 0 by default (disabled).
    -q, --quiet                    Quiet mode. No GPU stats at all.
        --hide-date                Don't show date in console.
        --no-color                 Disable color output for console.
        --no-clean-job             Don't drop stale shares.
        --no-hashrate-report       Disable hashrate report to pool.
        --no-nvml                  Disable NVML GPU stats.
        --no-strict-ssl            Disable certificate validation for SSL connections.
        --no-watchdog              Disable built-in watchdog.
        --watchdog-exit-mode       Specifies the action "A" the watchdog should take if the miner gets restarted "N" times
                                   within "M" minutes.
                                   Format: N:M:A. Valid values:
                                                  N: any positive integer,
                                                  M: any positive integer,
                                                  A: r(system reboot), s(system shutdown), e(miner exit)
                                   Actions "r" and "s" require running the miner with administrative privileges.
                                   Examples:
                                   20:10:s - watchdog will shutdown the system if the miner gets restarted 20 times
                                             within any 10 minute interval
                                   5:7:r   - watchdog will reboot the system if the miner gets restarted 5 times
                                             within any 7 minute interval

    -B, --benchmark                Benchmark mode.
        --benchmark-epoch          Epoch number used during benchmark (only for algorithms that generate DAG).
    -P, --protocol-dump            User protocol logging.
    -c, --config                   Load a JSON-format configuration file.
    -l, --log-path                 Full path of the log file.
        --cpu-priority             Set process priority (default: 2) 0 idle, 2 normal to 5 highest.

        --autoupdate               Perform auto update whenever a newer version of the miner is available.
        --back-to-main-pool-sec    Forces miner to switch back to main pool in case working with failover pool.
                                   Parameter is set in seconds. (default: 600)
        --exit-on-cuda-error       Forces miner to immediately exit on CUDA error.
        --exit-on-connection-lost  Forces miner to immediately exit on connection lost.
        --reconnect-on-fail-shares Forces miner to immediately reconnect to pool on N successively failed shares (default: 10).

        --fork-at                  Forces miner to change algorithm on predefined condition (works only with built-in watchdog enabled)
                                   Epoch condition: <algo_name>=epoch:<epoch_number> (eg: --fork-at etchash=epoch:390).
                                   Block condition: <algo_name>=block:<block_number> (eg: --fork-at x16rv2=block:6526421).
                                   Time condition:  <algo_name>=time:<YYYY-MM-DDTHH:MM:SS>. Time must be set in UTC+0.
                                   (eg: --fork-at x16rv2=time:2019-10-01T16:00:00).
                                   To change main pool port you must write it right after algo: <algo_name>:<port_number>
                                   (eg: --fork-at x16rv2:4081=time:2019-10-01T16:00:00).

        --mt                       Memory tweak mode (default: 0 - disabled). Range from 0 to 6. General recommendation
                                   is to start with 1, and then increase only if the GPU is stable.
                                   The effect is similar to that of ETHlargementPill.
                                   Supported on graphics cards with GDDR5 or GDDR5X memory only.
                                   Requires running the miner with administrative privileges.
                                   Can be set to a comma separated list to apply different values to different cards.
                                   Example: --mt 4 (applies tweak mode #4 to all cards that support this functionality)
                                            --mt 3,3,3,0 (applies tweak mode #3 to all cards except the last one)

        --script-start             Executes user script right after miner start (eg: --script-start path_to_user_script)
        --script-exit              Executes user script right before miner exit.
        --script-epoch-change      Executes user script on epoch change.
        --script-crash             Executes user script in case of miner crash.
        --script-low-hash          Executes user script in case of low hash. Hash threshold is set in MegaHashes/second.
                                   Example: --script-low-hash script_to_activate:50
                                            (activates "script_to_activate" script once total hashrate drops to 50MH/s)

        --version                  Display version information and exit.
    -h, --help                     Display this help text and exit.

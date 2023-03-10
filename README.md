# ed25519-gpu-vanity
This is a CUDA miner for ED25519 public keys.

I copied this from here: https://github.com/mcf-rocks/solanity

Then I made the following changes:
1. Implemented public keys verification for 4 bytes to be 0
2. Removed unnecessary base58 verification

When it finds a match, it will log a line starting with MATCH, you will see the vanity address found and the secret (seed) in hex.

This public key, when represented in HEX format, is the (vanity) address. The line you are looking for is immediatley after the match line, something like this:

[00000000dedbc57518eb1063b08f041391667b570bf94ae36be45a926639e73b]

NO WARRANTY OR LIABILITY WHATSOEVER, IN THIS WORLD OR THE WORLD TO COME, YOUR SOUL IS YOUR OWN RESPONSIBILITY.

The original instructions are reproduced below and are correct for build:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

# A CUDA based ed25519 vanity key finder (in HEX)

This is a GPU based vanity key finder. It does not currently use a CSPRNG and
any key generated by this tool is 100% not secure to use. Great fun for Tour de
Sol though.

## Configure
Open `src/config.h` and add any prefixes you want to scan for to the list.

## Building
Make sure your cuda binary are in your path, and build:

```bash
$ export PATH=/usr/local/cuda/bin:$PATH
$ make -j$(nproc)
```

## Running

```bash
LD_LIBRARY_PATH=./src/release ./src/release/cuda_ed25519_vanity
```


---
content_title: How to build eosio.contracts
link_text: How to build eosio.contracts
---

## Preconditions
Ensure the appropriate version of `eosio.cdt`, v1.6.x, is installed. Installing `eosio.cdt` from binaries is sufficient, follow the [`eosio.cdt` installation instructions steps](https://developers.eos.io/manuals/eosio.cdt/v1.6/index/#binary-releases) to install it. To verify if you have `eosio.cdt` installed and its version run the following command.

```sh
eosio-cpp -v
```

### Build contracts using the build script

#### To build contracts alone
Run the `build.sh` script in the top directory to build all the contracts.

#### To build the contracts and unit tests
1. Ensure the appropriate version of `eosio`, v1.8.x, has been built from source and installed. Installing `eosio` from binaries `is not` sufficient. You can find instructions on how to do it [here](https://developers.eos.io/manuals/eos/latest/install/build-from-source) in section `Building from Sources` but make sure you install the v1.8.x of `eosio` not any other version.
2. Run the `build.sh` script in the top directory with the `-t` flag to build all the contracts and the unit tests for these contracts.

### Build contracts manually

To build the `eosio.contracts` execute the following commands.

On all platforms except macOS:
```sh
cd you_local_path_to/eosio.contracts/
rm -fr build
mkdir build
cd build
cmake ..
make -j$( nproc )
cd ..
```

For macOS:
```sh
cd you_local_path_to/eosio.contracts/
rm -fr build
mkdir build
cd build
cmake ..
make -j$(sysctl -n hw.ncpu)
cd ..
```

### After build:
* If the build was configured to also build unit tests, the unit tests executable is placed in the _build/tests_ folder and is named __unit_test__.
* The contracts (both `.wasm` and `.abi` files) are built into their corresponding _build/contracts/\<contract name\>_ folder.
* Finally, simply use __cleos__ to _set contract_ by pointing to the previously mentioned directory for the specific contract.

# How to deploy the eosio.contracts

## To deploy eosio.bios contract execute the following command:
Let's assume your account name to which you want to deploy the contract is `testerbios`
```
cleos set contract testerbios you_local_path_to/eosio.contracts/build/contracts/eosio.bios/ -p testerbios
```

## To deploy eosio.msig contract execute the following command:
Let's assume your account name to which you want to deploy the contract is `testermsig`
```
cleos set contract testermsig you_local_path_to/eosio.contracts/build/contracts/eosio.msig/ -p testermsig
```

## To deploy eosio.system contract execute the following command:
Let's assume your account name to which you want to deploy the contract is `testersystem`
```
cleos set contract testersystem you_local_path_to/eosio.contracts/build/contracts/eosio.system/ -p testersystem
```

## To deploy eosio.token contract execute the following command:
Let's assume your account name to which you want to deploy the contract is `testertoken`
```
cleos set contract testertoken you_local_path_to/eosio.contracts/build/contracts/eosio.token/ -p testertoken
```

## To deploy eosio.wrap contract execute the following command:
Let's assume your account name to which you want to deploy the contract is `testerwrap`
```
cleos set contract testerwrap you_local_path_to/eosio.contracts/build/contracts/eosio.wrap/ -p testerwrap
```
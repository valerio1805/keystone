# How to build Keystone
## General Build
To build keystone components you have to execute in the `<BUILD>` directory:
```
/keystone/<BUILD>$ make
```
and then to update the image you have to run:
```
/keystone/<BUILD>$ make image
```

## Build of SDK
When you modify the files in `sdk` folder you have to execute:
```
/keystone/sdk/build$ make
/keystone/sdk/build$ make install
```
These commands will update the files of that libraries.

## Build of runtime and apps
When you modify the runtime you have to execute:
```
/keystone/<BUILD>/examples$ make clean
```
And then to build the changes in runtime and apps:
```
/keystone/<BUILD>$ make
/keystone/<BUILD>$ make examples
```

## Updating the enclave files
Firstly you have to update the files:
```
/keystone/<BUILD>$ make examples
```
After having built all the components you have to copy the enclave files into `/keystone/<BUILD>/overlay/root`:
```
/keystone/<BUILD>$ find ./examples/ -name '*.ke' -exec cp \{\} ./overlay/root/ \;
/keystone/<BUILD>$ cp sm.build/platform/generic/firmware/fw_payload.bin overlay/root/
```
At the end you need to update the image:
```
/keystone/<BUILD>$ make image
```

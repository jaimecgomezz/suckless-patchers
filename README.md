# suckless-patchers

Simple utilities that will take care of patches for you. Lets make `suckless software for everybody`.



## Supported tools

[dmenu](https://github.com/jaimecgomezz/dmenu), [st](https://github.com/jaimecgomezz/st)



## Patching

[handle](https://github.com/jaimecgomezz/dmenu/blob/master/handle) will patch your distro, just run:

```sh
# Usage: ./handle ACTION PATCH [OPTIONS]

# Installing patch A
./handle patch A

# Removing border A
./handle depatch A
```

The rest of ACTIONS, PATCHES and OPTIONS available on any distro can be found running:

```sh
./handle
```



## Testing patches

For those willing to support the projects, the [test-patch](https://github.com/jaimecgomezz/dmenu/blob/master/test-patch) script is your friend. It will test the integration of a given patch with the rest of patches listed under the `patches` folder. Whenever you need know if the patch you’ve been working on its ready, use it!

`````sh
# Usage: ./test-patch PATCH

# Testing the patch A
./test-patch A
...
B			Ok	# Means both patches can be used simultaneously
C			Failed!	# Means that the both patches have conflicts integrating together
...
`````

When the tests are finished, `test-patch` will report the results, which should be included in your PR. If a patch “fails” you should:

- Make the older patch compatible with the new patch. Not on a functional level, but in a code level.
- Warn about the incompatibility of both patches in the `handle-usage` doc.

WARNING: This utility DO NOT test the patch functionality (if it does whats it’s suppose to do), it only makes you aware of any patch that might have troubles integrating with it .



## Installation

```sh
# Assuming your suckless distros are in ~/
git clone https://github.com/jaimecgomezz/suckless-patchers.git

# Copy the 'handle' utility to the 'dmenu' distro
cp ~/suckless-patchers/handle ~/dmenu
```

And that’s it! You can repeat this steps on every available distro listed at the beginning.

Running `handle` will output something different on each one, this is because they all source a file called `handle-usage` which lists all the patches available for that specific distro.

 




## Contributing

You can read the `CONTRIBUTING` and make a `PR` whenever you’re ready, they are all welcomed:)



## License

Code released under the MIT license.

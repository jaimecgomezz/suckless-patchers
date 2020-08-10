# suckless-patchers

Simple utilities that will take care of patches for you. Lets make `suckless software for everybody`.



## Supported tools

[dmenu](https://github.com/jaimecgomezz/dmenu), [st](https://github.com/jaimecgomezz/st)



## Installation

```sh
# Assuming your suckless distros are in ~/
git clone https://github.com/jaimecgomezz/suckless-patchers.git

# Copy the 'handle' utility to the 'dmenu' distro
cp ~/suckless-patchers/handle ~/dmenu

# Copy the 'test-patch' utility to the 'dmenu' distro (optional)
cp ~/suckless-patchers/test-patch ~/dmenu
```

And that’s it! You can repeat the last steps on every available distro listed under the [Supported tools](https://github.com/jaimecgomezz/suckless-patchers#supported-tools) section.



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

For those willing to support the projects, the [test-patch](https://github.com/jaimecgomezz/dmenu/blob/master/test-patch) script is your friend. It will test your patch against the rest listed under the `patches` folder. Use it whenever your patch is ready!

`````sh
# Usage: ./test-patch PATCH

# Testing the patch A
./test-patch A
...
B			Ok	# Means both patches (A & B) can be used simultaneously
C			Failed!	# Means both patches (A & C) have conflicts integrating together
...
`````

When the tests are finished, `test-patch` will report the results (which should be included in your PR).

Note: `test-patch` WONT test your patch functionality (if it does whats it’s suppose to do), it only makes you aware of patches that might be interfering with it (e.g., those that modify the same line of code)   

If a patch fails you should:

- [Make patches compatible](https://github.com/jaimecgomezz/dmenu#making-patches-compatible).
- Warn about the functional incompatibility of both patches in the `handle-usage` doc,  see [this example](https://github.com/jaimecgomezz/dmenu/commit/0837f8e89ff01dc83577f5ad7d373dc436270e1c?short_path=04c6e90#diff-402500c027bafa15c6dcc413f6e48ab7).



## Making patches compatible

Take a look at these [code](https://github.com/jaimecgomezz/dmenu/blob/0a2fce0fefe945ac724bae3a71d85a303f7fa878/dmenu.c#L263-L270). At that moment the [grid patch](https://github.com/jaimecgomezz/dmenu/blob/master/patches/grid.patch) was already implemented, the next was the [vertfull patch](https://github.com/jaimecgomezz/dmenu/blob/master/patches/vertfull.patch). They both modify [dmenu](https://github.com/jaimecgomezz/dmenu) in a similar way so they `can't be used simultaneously`. Nevertheless, you should be able to use one or another, so they should integrate together, at list in code. To make them compatible some [changes](https://github.com/jaimecgomezz/dmenu/commit/50433eff0db31f3b7e4c1312bae977b8d7ec7246) were done, so now the `vertfull patch` can be implemented like [this](https://github.com/jaimecgomezz/dmenu/commit/0eb115af90dc06b099e2009abf4f35b0ff19e663).

Of course you can create an issue if something wasn’t clear enough, I’ll be glad to help!




## Contributing

You can read the `CONTRIBUTING` and make a `PR` whenever you’re ready, they are all welcomed:)



## License

Code released under the MIT license.

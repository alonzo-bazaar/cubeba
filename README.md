# cubeba
Wrapper around stm32 cube cli, because the cube cli is amazing for existing but the interface itself is kind of a pain in the ass (and very beta).

This project was developed as in internal tool for usage within the firenze race team but I decided to make it public because I thought it would look cool on my resume (and be useful to somebody probably).

`cubeba` handles
- installing shit (cube bundles and the like)
- compiling the fucking thing
- flashing the fucking thing
- running the fucking thing (ie: start a debugger server you connect to with `gdb` or whatever)

# usage
## adding to your project
To add `cubeba` to an stm32 project using the `cube` cli, all you need to do is copy the `cubeba` script into your stm32 project's root directory (the one with the `.ioc` file and all the other root shit), the script has no external dependencies beyond the `cube` cli, and perl5's core modules.

> **NOTE:** although it is very unlikely that the perl distribution for your system comes without core its modules, it is not impossible,
> any desktop OS is quite unlikely to elide a core module from its perl package, but docker images, for instance, will will often remove some core modules from their perl to keep the image leaner.
> This isn't really a problem if you can change the `Dockerfile` since perl's core modules are gonna be in the repos of whatever distro the image isbased on anyway.

## subcommands and flags and shit
The following commands are supported
```sh
./cubeba build # builds program
./cubeba flash # flashes thi
./cubeba debug # runs debug server
```
Running `./cubeba` with no flags defaults to `./cubeba build`.  
`cubeba` will assume you're compiling using the `'Debug'` target/preset/whatever it's called, unless otherwise specified by passing `-r` or `--release`, in which case it will be `'Release'`.
The `-v` and `--verbose` flags can also be passed to get a log of everything `cubeba` is doing (currently logged to stdout).

## honoured environment variables
`cubeba` will try to automatically detect the project's name by looking for any `.ioc` files present in the same directory as itself.
Note this will only work if there is one and only one `.ioc` file in the project root, also note that some weird shit may go down if the `.ioc` file has a different name from that of your project.

Now, if for whatever reason, your project's name is different from the name of any `.ioc` file in the project root, and/or you have multiple `.ioc` files in the project root, you can still use `cubeba` in the project by setting the `CUBEBA_PROJECT` environment variable before you run `cubeba`, if this environment variable is set `cubeba` will skip any check on `.ioc` files and whatnot, and just use the value of `CUBEBA_PROJECT` to determine the project name.

# namesake
`cubeba` is named after how [kibbeh](https://en.wikipedia.org/wiki/Kibbeh) (a kind of meatball) is called in egyptian arabic (*kobeba*).  
I needed a pun with `cube` and [qbert](https://en.wikipedia.org/wiki/Q*bert) was too obious

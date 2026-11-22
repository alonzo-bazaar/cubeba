# cubeba
Wrapper around stm32 cube cli, because the cube cli is amazing for existing but the interface itself is kind of a pain in the ass (and very beta).

This project was developed as in internal tool for usage within the firenze race team but I decided to make it public because I thought it would look cool on my resume.

Cubeba handles
- installing shit (cube bundles and the like)
- compiling the fucking thing
- flashing the fucking thing
- running the fucking thing (debugger server)

# usage
## subcommands and flags and shit
The following commands are supported
```sh
./cubeba build # builds program
./cubeba flash # flashes thi
./cubeba debug # runs debug server
```

running `./cubeba` by itself defaults to `./cubeba build`

cubeba will assume you're compiling using the `'Debug'` target/preset/whatever it's called, unless otherwise specified by passing `-r` or `--release`, in which case it will be `'Release'`

`-v` and `--verbose` can also be used to get a lot of everything cubeba is doing (to stdout)

## using in your project
you will find the following two lines of code in the `cubeba` script
```perl
my $PROJECT_NAME='AMS';
my @REQUIRED_BUNDLES=('cmake', 'stlink-gdbserver', 'programmer');
```

Just change that to your own project's name and voila this shit isn't big enough to warrant a config file.

> **NOTE 1:** `@REQUIRED_BUNDLES` contains the bundles needed by `cubeba` to do its thing, these may or may not overlap with the bundles installed by
> ```
> cube bundle install --project
> ```
> but they're handled separately to make sure that, regardless of what your project
> bundles are, `cubeba` can still compile and flash and shit

> **NOTE 2:** could this have been implmented with `glob("./*.ioc")`... yes
> I should probably do that tbh

# namesake
cubeba is named after how https://en.wikipedia.org/wiki/Kibbeh is called in egyptian arabic (*kobeba*).  
I needed a pun with `cube` and [qbert](https://en.wikipedia.org/wiki/Q*bert) was too obious



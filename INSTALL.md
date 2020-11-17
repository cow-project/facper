# Install Go

[Install Go, set the `GOPATH`, and put `GOPATH/bin` on your `PATH`](https://github.com/facper/facper/wiki/Setting-GOPATH).

# Install facper

You should be able to install the latest with a simple `go get -u github.com/facper/facper/cmd/facper`.
The `-u` makes sure all dependencies are updated as well.

Run `facper version` and `facper --help`.

If the install falied, see [vendored dependencies below](#vendored-dependencies).

To start a one-node blockchain with a simple in-process application:

```
facper init
facper node --proxy_app=dummy
```

See the [application developers guide](https://github.com/facper/facper/wiki/Application-Developers) for more details on building and running applications.


## Vendored dependencies

If the `go get` failed, updated dependencies may have broken the build.
Install the correct version of each dependency using `glide`.

Fist, install `glide`:

```
go get github.com/Masterminds/glide
```

Now, fetch the dependencies and install them with `glide` and `go`:

```
cd $GOPATH/src/github.com/facper/facper
glide install
go install ./cmd/facper
```

Sometimes `glide install` is painfully slow. Hang in there champ.

The latest facper Core version is now installed. Check by running `facper version`.

## Troubleshooting

If `go get` failing bothers you, fetch the code using `git`:

```
mkdir -p $GOPATH/src/github.com/facper
git clone https://github.com/facper/facper $GOPATH/src/github.com/facper/facper
cd $GOPATH/src/github.com/facper/facper
glide install
go install ./cmd/facper
```

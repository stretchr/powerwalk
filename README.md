# Powerwalk

Go package for concurrently walking files.

## Usage

Powerwalk is a drop-in replacement for the `filepath.Walk` method, and so has the same signature, even using the `filepath.WalkFunc` too.

```
powerwalk.Walk(root string, walkFn filepath.WalkFunc) error
```

By default, Powerwalk will call the `walkFn` for `powerwalk.DefaultConcurrentWalks` (currently `100`) files at a time.  To be specific about the number of concurrent files to walk, use the `WalkLimit` alternative.

```
WalkLimit(root string, walkFn filepath.WalkFunc, limit int) error
```

The `WalkLimit` function does the same as `Walk`, except allows you to specify the number of files to concurrently walk using the `limit` argument.  The `limit` argument must be one or higher (i.e. `>0`).  Specificying a limit that's too high, causes unnecessary overhead so sensible numbers are encouraged.
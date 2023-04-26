# ReadWriteLocks

[![CI](https://github.com/Invenia/ReadWriteLocks.jl/workflows/CI/badge.svg)](https://github.com/Invenia/ReadWriteLocks.jl/actions?query=workflow%3ACI)
[![codecov.io](https://codecov.io/github/invenia/ReadWriteLocks.jl/coverage.svg?branch=master)](https://codecov.io/github/invenia/ReadWriteLocks.jl?branch=master)

## Usage

```julia
using ReadWriteLocks

# The type provided by this package is ReadWriteLock.
rwlock = ReadWriteLock()

# This lock provides access to a read lock and a write lock
rlock = get_read_lock(rwlock)
wlock = get_write_lock(rwlock)

# To acquire a read lock:
lock(rlock)

# To release a read lock:
unlock(rlock)

#=
Write locks provide the same interface.

You can acquire any number of read locks at a time.
A read lock will block if a write lock has been acquired.
A write lock will block if a read lock or write lock has been acquired.
=#
```

## Compatibility

This package is meant to be compatible with Julia's lightweight threads (where it is not strictly necessary) and true multithreaded Julia, in order to facilitate unified codebases that support future thread-safety.

## License

ReadWriteLocks.jl is provided under the MIT "Expat" License.

## Citation

This is largely based upon the original Java source from:
> M. Herlihy and N. Shavit, “8.3.1 Simple Readers-Writers Lock,” in The art of multiprocessor programming, revised first edition, Rev. 1st., Waltham, Massachusetts: Morgan Kaufmann, 2012, pp. 184–185.

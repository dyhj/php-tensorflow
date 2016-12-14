TensorFlow PHP Extension
========================

use `tensorflow` `0.12.0-rc0` c api.

## Requirements

- [bazel](https://www.bazel.build/versions/master/docs/install.html)
- Environment to build TensorFlow from source code
  ([Linux](https://www.tensorflow.org/versions/master/get_started/os_setup.html#prepare-environment-for-linux)
  or [Mac OS
  X](https://www.tensorflow.org/versions/master/get_started/os_setup.html#prepare-environment-for-mac-os-x)).
  If you'd like to skip reading those details and do not care about GPU
  support, try the following:

  ```sh
  # On Linux
  sudo apt-get install python swig python-numpy

  # On Mac OS X with homebrew
  brew install swig
  ```

## Installation

1. Download and Build the TensorFlow by Git Submodule.

   ```sh
   git submodule update --init --recursive
   cd lib/tensorflow
   ./configure
   bazel build -c opt //tensorflow:libtensorflow.so
   cp bazel-bin/tensorflow/libtensorflow.so /usr/local/lib
   ```

2. Build the PHP Extension

   ```sh
   phpize
   ./configure
   make install
   ```

## Contributions

This API has been built on top of the [C API](https://www.tensorflow.org/code/tensorflow/c/c_api.h),
which is intended for building language bindings for TensorFlow functionality.
However, this is far from complete. Contributions are welcome.

## Documents

Current useable stuffs.

```php
<?php
namespace TensorFlow
{
    const VERSION;

    const DTYPE_FLOAT = 1;
    const DTYPE_DOUBLE = 2;
    const DTYPE_INT32 = 3;
    const DTYPE_UINT8 = 4;
    const DTYPE_INT16 = 5;
    const DTYPE_INT8 = 6;
    const DTYPE_STRING = 7;
    const DTYPE_COMPLEX64 = 8;
    const DTYPE_COMPLEX = 8;
    const DTYPE_INT64 = 9;
    const DTYPE_BOOL = 10;
    const DTYPE_QINT8 = 11;
    const DTYPE_QUINT8 = 12;
    const DTYPE_QINT32 = 13;
    const DTYPE_BFLOAT16 = 14;
    const DTYPE_QINT16 = 15;
    const DTYPE_QUINT16 = 16;
    const DTYPE_UINT16 = 17;
    const DTYPE_COMPLEX128 = 18;
    const DTYPE_HALF = 19;
    const DTYPE_RESOURCE = 20;

    class Status
    {
        public function setCode(int $code, string $message = ""): void;
        public function getCode(): int;
        public function getMessage(): string;
    }

    class Buffer
    {
        public function __construct(string $buffer);
        public function __toString(): string;
    }

}
```

## Reference

- [TensorFlow Go API](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/go)

## Todo

- [Operator Overloading](https://github.com/php/pecl-php-operator)

# hunter with ceres-sover

This project is a minimal example on how to use [Hunter](https://github.com/cpp-pm/hunter) to get [ceres-solver](https://github.com/ceres-solver/ceres-solver) as a build dependency.

For this to work you only need `CMake` and a compiler (`gcc, `clang`, `msvc`). When building with SuiteSparse support a Fortran compiler is also required for the `LAPACK` dependency (except on `msvc`, Hunter provides a prebuilt dll for that case)


## Build it
Minimal build (no SuiteSparse support)
```
cmake -H. -B_build -DHUNTER_CERES_WITH_SUITESPARSE=OFF -DCMAKE_BUILD_TYPE=Release
cmake --build _build
```

To tell Hunter to build with SuiteSparse use the custom option `HUNTER_CERS_WITH_SUITESPARSE=ON`.
This is a custom option setting the needed flags in [cmake/Hunter/config.cmake](cmake/Hunter/config.cmake).
```
cmake -H. -B_build -DHUNTER_CERES_WITH_SUITESPARSE=ON -DCMAKE_BUILD_TYPE=Release
cmake --build _build
```

On MSVC the generator expression must be specified as well.
See https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html#visual-studio-generators for options.

```
cmake -H. -B_build -G "Visual Studio 15 2017 Win64" -DHUNTER_CERES_WITH_SUITESPARSE=ON
cmake --build _build --config Release
```


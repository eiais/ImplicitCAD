# Version [next](https://github.com/Haskell-Things/ImplicitCAD/compare/v0.4.1.0...master) (202Y-MM-DD)

* ExtOpenScad interface changes
  * Added `projection(cut=true)` support [#448](https://github.com/Haskell-Things/ImplicitCAD/pull/448)

* Haskell interface changes
  * `extrude` arguments are now swapped, instead of `extrude obj height` we now have `extrude height obj` [#473](https://github.com/Haskell-Things/ImplicitCAD/issues/473)
  * Added `slice` primitive [#448](https://github.com/Haskell-Things/ImplicitCAD/pull/448)
  * Added `boxFrame` and `link` primitive [#471](https://github.com/Haskell-Things/ImplicitCAD/pull/471)

* Other changes
  * Fixing `shell` so that it doesn't increase the outside dimentions of objects.
  * Fixing an issue with bounding boxes for infinite functions. [#412](https://github.com/Haskell-Things/ImplicitCAD/issues/412)
  * Making `torus` and `ellipsoid` primitive objects, rather than being defined implicitly. [#450](https://github.com/Haskell-Things/ImplicitCAD/issues/450)
  * Improved formatting of ExtOpenSCAD code [#472](https://github.com/Haskell-Things/ImplicitCAD/pull/472)
  * Fixing an issue where ImplicitCAD extended primitive objects were being exported to OpenSCAD where they aren't supported.

# Version [0.4.1.0](https://github.com/Haskell-Things/ImplicitCAD/compare/v0.4.0.0...v0.4.1.0) (2023-12-18)

* ExtOpenScad interface changes
  * Added `rands` and `lookup` support [#433](https://github.com/Haskell-Things/ImplicitCAD/pull/433)
  * Added several primitives
    * `cone(r, h, center)`
    * `torus(r1, r2)`
    * `ellipsoid(a, b, c)`
  * Adding vector-matrix, matrix-vector, and matrix-matrix multiplication support to `*` [#414](https://github.com/Haskell-Things/ImplicitCAD/issues/414)
  * Several mathematical functions that have undefined values for some inputs or tend to infinity have been given finite but extremely large bounds.

* Haskell interface changes
  * Added matching primitives for `cone`, `torus`, and `ellipsoid`
  * Adding vector-matrix, matrix-vector, and matrix-matrix multiplication support to `mult` [#414](https://github.com/Haskell-Things/ImplicitCAD/issues/414)

* Other changes
  * Migrating StateC and StateE to a ReaderT/WriterT/StateT transformer stack, rather than being just StateT. [#432](https://github.com/Haskell-Things/ImplicitCAD/pull/432)
  * Fixing an off by one error in variable stack lookups. [#431](https://github.com/Haskell-Things/ImplicitCAD/issues/431)
  * Fixing exponent operator precedence. [#428](https://github.com/Haskell-Things/ImplicitCAD/issues/428)
  * Fixing some crashes relating to unclosed loops when generating surfaces. [#373](https://github.com/Haskell-Things/ImplicitCAD/issues/373)
  * Addition of canonicalization pass and `canonicalize` member function for `Object` [#445](https://github.com/Haskell-Things/ImplicitCAD/pulls/445)

# Version [0.4.0.0](https://github.com/Haskell-Things/ImplicitCAD/compare/v0.3.0.0...v0.4.0.0) (2022-06-06)

* Changelog started. Previous release was `0.3.0.1`.

* Haskell interface changes
  * Added support for XY-scaling on `linear_extrude` [#269](https://github.com/Haskell-Things/ImplicitCAD/pull/269)
    * `ExtrudeRM` scale type changes from `(Either ℝ (ℝ -> ℝ))` to `ExtrudeRMScale`
  * Replaced the Rect primitives with SquareR and CubeR [#296](https://github.com/Haskell-Things/ImplicitCAD/pull/296)
    * `squareR` and `cubeR` are now available
  * Added support for mirroring objects around axis using `mirror` function [#300](https://github.com/Haskell-Things/ImplicitCAD/pull/300)
  * `differenceR` changes type to require mandatory shape to substract from [#294](https://github.com/Haskell-Things/ImplicitCAD/pull/294)
    * from `Object obj vec => R -> [obj] -> obj`
    * to `Object obj vec => R -> obj -> [obj] -> obj`
  * Both `SymbolicObj2` and `SymbolicObj3` now have `Semigroup` and `Monoid` instances, where `<>` acts as `union` [#301](https://github.com/Haskell-Things/ImplicitCAD/pull/301)
  * Added `rotateQ` function for rotating with Quaternions [#314](https://github.com/Haskell-Things/ImplicitCAD/pull/314)
  * `ℝ2` and `ℝ3` are now using `V2` and `V3` from `linear` instead of tuples [#342](https://github.com/Haskell-Things/ImplicitCAD/pull/342)
  * Rounding is now separate from primitives [#362](https://github.com/Haskell-Things/ImplicitCAD/pull/362)
    * Introduces `withRounding` function.
    * Instead of `primitiveR roundingValue ...` we now use `withRounding roundingValue (primitive ...)`
    * Replaces `squareR`, `rectR`, `polygonR`, `cubeR`, `rect3R`, `extrudeR`, `extrudeRM` with versions
      without rounding arugment (`square`, `rect`, ...).
  * Removed `ExtrudeRotateR` [#365](https://github.com/Haskell-Things/ImplicitCAD/pull/365)
  * `rotateExtrude` now longer accepts rounding paramater [#367](https://github.com/Haskell-Things/ImplicitCAD/pull/367)
  * Added `transform3` (transform using 4x4 matrix representing affine transformation) [#410](https://github.com/Haskell-Things/ImplicitCAD/pull/410)
  * Changed `Object obj vec` class to `Object obj f a` [#420](https://github.com/Haskell-Things/ImplicitCAD/pull/420)

* ExtOpenSCAD interface changes
  * `scale` function with single parameter now behaves similar to OpenSCAD one [#258](https://github.com/Haskell-Things/ImplicitCAD/pull/258)
    * scales 2D object in both dimensions
  * `rotateExtrude` angle `a` parameter renamed to `angle` to match OpenSCAD [#259](https://github.com/Haskell-Things/ImplicitCAD/pull/259)
  * Added `mirror` support [#300](https://github.com/Haskell-Things/ImplicitCAD/pull/300)
  * Added `multmatrix` support [#410](https://github.com/Haskell-Things/ImplicitCAD/pull/410)

* Other changes
  * Fixed the ExtOpenSCAD lexer bug where newlines were part of identifiers [#256](https://github.com/Haskell-Things/ImplicitCAD/pull/256)
  * `implicitsnap` not built by default anymore [#272](https://github.com/Haskell-Things/ImplicitCAD/pull/272)
    * Can be enabled again with `cabal configure --flag=implicitsnap`
  * Fixed vertex coordinates of OBJ output [#281](https://github.com/Haskell-Things/ImplicitCAD/pull/281)
    * `discreteAprox` of `NormedTriangleMesh` now runs in parallel [#282](https://github.com/Haskell-Things/ImplicitCAD/pull/282)
  * Binaries now built with default `-rtsopts "-with-rtsopts -N -qg -t"` to allow automatic parallelization
  * Added haddocks for Haskell eDSL [#284](https://github.com/Haskell-Things/ImplicitCAD/pull/284) & [#287](https://github.com/Haskell-Things/ImplicitCAD/pull/287)
  * Added golden test machinery [#311](https://github.com/Haskell-Things/ImplicitCAD/pull/311)
  * Added quickcheck test machinery for implicit functions [#316](https://github.com/Haskell-Things/ImplicitCAD/pull/316)
  * Rotate now internally uses quaternions [#314](https://github.com/Haskell-Things/ImplicitCAD/pull/314)
  * Fixes to triangle generation [#355](https://github.com/Haskell-Things/ImplicitCAD/pull/355) and [#375](https://github.com/Haskell-Things/ImplicitCAD/pull/375)
  * ExtOpenSCAD vector addition [#408](https://github.com/Haskell-Things/ImplicitCAD/pull/408)

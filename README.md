# Eigen Recursive Matrix Extension (ERME)

ERME is an extension to the [Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page) math library for recursive linear algebra. 

Features
 * Template specializations to allow the creation and usage of recursive matrix types
 * Support for recursive sparse matrices (for example a block-sparse matrix)
 * A recursive LDLT decomposition, based on Eigen's simplicial implemenation
 * Mixed matrix types and mixed recursive solvers for structured optimization problems
 
 <img src="data/1.png" width="425"/> <img src="data/2.png" width="425"/> 
  <img src="data/ba_table.png" width="800"/>
## Usage
	
        // See samples/helloRecursive for the full example
        #include "EigenRecursive/All.h"
        int main(int, char**)
        {
             using namespace Eigen;
             using namespace Eigen::Recursive;

             using Block          = Matrix<double, 2, 2>;
             using MatrixOfMatrix = Matrix<MatrixScalar<Block>, 2, 2>;

             MatrixOfMatrix A, B, C;
             setRandom(A);
             setRandom(B);

             C = A * B;

             std::cout << C << std::endl;
             return 0;
        }
    
## Samples and Benchmarks

Compile and run instructions:

        mkdir build
        cd build
        cmake ..
        make -j8
        ./helloRecursion

Sparse Block benchmark:

 * Install the MKL library and make sure it is found by cmake.
 * Compile in Release mode. (I currently recommend to use the latest Clang compiler)
 
 Bundle Adjustment:
 * Install Sophus from source: [Link](https://github.com/strasdat/Sophus)

Other examples (included in the [Saiga](https://github.com/darglein/saiga) library):
 * [Benchmark - LDLT - Cholmod](https://github.com/darglein/saiga/tree/master/samples/vision/sparse_ldlt)
 * [Pose Graph Optimization](https://github.com/darglein/saiga/blob/master/src/saiga/vision/pgo/PGORecursive.h)
  * [ARAP](https://github.com/darglein/saiga/blob/master/src/saiga/vision/arap/RecursiveArap.h)
	
## License

This project contains (modified) code from the Eigen library. You can find the Eigen license [here](http://eigen.tuxfamily.org/index.php?title=Main_Page#License).

All of our code is under the MIT License. See the LICENSE file for more information.

Copyright (c) 2019 Darius Rückert <darius.rueckert@fau.de>



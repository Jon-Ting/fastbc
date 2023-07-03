# FastBC

## Description

`FastBC` is a repository containing the C++ codes required for the computation of box-counting dimension of the point cloud representation of the surface of interest of a given 3D object consisting of overlapping spherical entities, a functionality offered by the [`Sphractal`](https://sphractal.readthedocs.io/en/latest/) Python package. 

Once compiled successfully, the executable takes in the following as input argument:
* Resolution of the 3D binary image (int).
* Name of input file name (str) containing the indices of the occupied voxels.
* Name of output file name (str) storing the box counts corresponding to each box length.

And runs the box-counting algorithm on the 3D binary image computed based onn the indices of voxels read from the input file, and outputs the box counts corresponding to each box length used to an output file with the specified name.

It was built upon the work of [Juan Ruiz de Miras et al.](https://www.sciencedirect.com/science/article/pii/S1877750322002678), who distributed their source codes freely as [Fast Box-Counting Algorithm](https://www.ugr.es/~demiras/fbc/). The following files in this repository are obtained from [Fast Box-Counting Algorithm (October 2022 version)](https://www.ugr.es/~demiras/fbc/):
  - bcCPU.cpp and bcCPU.h: C++ files with the implementation on CPU of the box-counting algorithm for binary 2D, 3D and 4D data
  - bcCUDA3D.cu and bcCUDA3D.cuh: CUDA/C++ files with the implementation on GPU of the box-counting algorithm for binary 3D data

## Usage and Compilation

Users need to compile either `3DbinImBCcpu.cpp` or `3DbinImBCgpu.cpp` into an executable on their machine and pass the path to the executable to the function `sphractal.runBoxCnt()` or `sphractal.getVoxelBoxCnts()` if the computation of the box-counting dimension of the point cloud representation of the surface of interest is desired.

`3DbinImBCcpu.cpp` could be compiled by appropriate C++ compilers. 
```bash
$ g++ 3DbinImBCcpu.cpp bcCPU.cpp -o 3DbinImBCcpu.exe
```

`3DbinImBCgpu.cpp` requires the following for successful compilation:
  - Machine with a capable [CUDA GPU](https://developer.nvidia.com/cuda-gpus)
  - [CUDA SDK Toolkit](https://developer.nvidia.com/cuda-toolkit)
```bash
$ nvcc -O3 3DbinImBCgpu.cpp bcCUDA3D.cu -o 3DbinImBCgpu.exe
```

## License

The original work from which this work was derived from was distributed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/). Under the ShareAlike term of this license, this work is also distributed under the same license as the original. To view a copy of this license, visit http://creativecommons.org/licenses/by-sa/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.

## Credits/Citations

This work was built upon the publication below:
"Fast Computation of Fractal Dimension for 2D, 3D and 4D Data" 
Juan Ruiz de Miras, Miguel Ángel Posadas, Antonio José Ibáñez-Molina, María Felipa Soriano and Sergio Iglesias-Parro
Journal of Computational Science 66, 2023
DOI: https://doi.org/10.1016/j.jocs.2022.101908

## Contact

Email: `Jonathan.Ting@anu.edu.au`/`jonting97@gmail.com`

Feel free to reach out if you have any questions, suggestions, or feedback.

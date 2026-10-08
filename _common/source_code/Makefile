# Copyright (c) 2020 NVIDIA Corporation.  All rights reserved. 

CC := nvc++
CFLAGS := -O3 -w -ldl
# Root of the NVIDIA HPC SDK release in use, for example
# /opt/nvidia/hpc_sdk/Linux_x86_64/26.5. If NVHPC_ROOT is already set in the
# environment (the course image sets it, and so do NVIDIA's "nvhpc" modules)
# that value is used; otherwise it is worked out from where nvc++ is on PATH.
# Nothing here names an SDK version or an install location.
NVHPC_ROOT ?= $(abspath $(dir $(shell command -v nvc++ 2>/dev/null))../..)
NVTXLIB_c := -I$(NVHPC_ROOT)/cuda/include

FC := nvfortran
FLAGS := -O3 -w 
NVTXLIB_f := -lnvhpcwrapnvtx

rdf_f:rdf.f90
	${FC} ${FLAGS} rdf.f90 -o rdf_f ${NVTXLIB_f} 
    
    
rdf_c: rdf.cpp
	${CC} ${CFLAGS} -o rdf_c rdf.cpp ${NVTXLIB_c} 

clean:
	rm -f *.o rdf_c rdf_f

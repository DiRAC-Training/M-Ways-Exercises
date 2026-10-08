# Copyright (c) 2020 NVIDIA Corporation.  All rights reserved. 

FC := nvfortran
CC := nvc++

FLAGS := -O3 -w 
ACCFLAGS := -acc=multicore -Minfo=accel

NVTXLIB_F := -lnvhpcwrapnvtx

# Root of the NVIDIA HPC SDK release in use, for example
# /opt/nvidia/hpc_sdk/Linux_x86_64/26.5. If NVHPC_ROOT is already set in the
# environment (the course image sets it, and so do NVIDIA's "nvhpc" modules)
# that value is used; otherwise it is worked out from where nvc++ is on PATH.
# Nothing here names an SDK version or an install location.
NVHPC_ROOT ?= $(abspath $(dir $(shell command -v nvc++ 2>/dev/null))../..)
NVTXLIB_C := -I$(NVHPC_ROOT)/cuda/include

rdf_f: rdf.f90
	${FC} ${FLAGS} ${ACCFLAGS} -o rdf_f rdf.f90 ${NVTXLIB_F} 

rdf_c: rdf.cpp
	${CC} ${FLAGS} ${ACCFLAGS} -o rdf_c rdf.cpp ${NVTXLIB_C} 

clean:
	rm -f *.o rdf_f rdf_c

FROM 665761212904.dkr.ecr.us-east-2.amazonaws.com/kflansburg/cuda:11.4.1-base-ubuntu20.04

ENV NV_CUDA_LIB_VERSION 11.4.1-1

ENV NV_NVTX_VERSION 11.4.100-1
ENV NV_LIBNPP_VERSION 11.4.0.90-1
ENV NV_LIBCUSPARSE_VERSION 11.6.0.100-1

ENV NV_LIBCUBLAS_PACKAGE_NAME libcublas-11-4
ENV NV_LIBCUBLAS_VERSION 11.5.4.8-1
ENV NV_LIBCUBLAS_PACKAGE ${NV_LIBCUBLAS_PACKAGE_NAME}=${NV_LIBCUBLAS_VERSION}

ENV NV_LIBNCCL_PACKAGE_NAME libnccl2
ENV NV_LIBNCCL_PACKAGE_VERSION 2.10.3-1
ENV NCCL_VERSION 2.10.3-1
ENV NV_LIBNCCL_PACKAGE ${NV_LIBNCCL_PACKAGE_NAME}=${NV_LIBNCCL_PACKAGE_VERSION}+cuda11.4

LABEL maintainer "NVIDIA CORPORATION <cudatools@nvidia.com>"

RUN apt-get update && apt-get install -y --no-install-recommends \
    cuda-libraries-11-4=${NV_CUDA_LIB_VERSION} \
    libnpp-11-4=${NV_LIBNPP_VERSION} \
    cuda-nvtx-11-4=${NV_NVTX_VERSION} \
    libcusparse-11-4=${NV_LIBCUSPARSE_VERSION} \
    ${NV_LIBCUBLAS_PACKAGE} \
    ${NV_LIBNCCL_PACKAGE} \
    && rm -rf /var/lib/apt/lists/*

RUN echo "baz"

# Keep apt from auto upgrading the cublas and nccl packages. See https://gitlab.com/nvidia/container-images/cuda/-/issues/88
RUN apt-mark hold ${NV_LIBCUBLAS_PACKAGE_NAME} ${NV_LIBNCCL_PACKAGE_NAME}

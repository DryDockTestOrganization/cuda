ARG IMAGE_NAME
FROM ${IMAGE_NAME}:11.4.1-runtime-centos7 as base

FROM base as base-amd64

ENV NV_CUDA_LIB_VERSION 11.4.1-1
ENV NV_NVPROF_VERSION 11.4.100-1
ENV NV_CUDA_CUDART_DEV_VERSION 11.4.108-1
ENV NV_NVML_DEV_VERSION 11.4.43-1
ENV NV_LIBCUBLAS_DEV_VERSION 11.5.4.8-1
ENV NV_LIBNPP_DEV_VERSION 11.4.0.90-1



FROM base-${TARGETARCH}

ARG TARGETARCH

LABEL maintainer "NVIDIA CORPORATION <sw-cuda-installer@nvidia.com>"

RUN yum install -y \
    make \
    cuda-command-line-tools-11-4-${NV_CUDA_LIB_VERSION} \
    cuda-libraries-devel-11-4-${NV_CUDA_LIB_VERSION} \
    cuda-minimal-build-11-4-${NV_CUDA_LIB_VERSION} \
    cuda-cudart-devel-11-4-${NV_CUDA_CUDART_DEV_VERSION} \
    cuda-nvprof-11-4-${NV_NVPROF_VERSION} \
    cuda-nvml-devel-11-4-${NV_NVML_DEV_VERSION} \
    libcublas-devel-11-4-${NV_LIBCUBLAS_DEV_VERSION} \
    libnpp-devel-11-4-${NV_LIBNPP_DEV_VERSION} \
    && yum clean all \
    && rm -rf /var/cache/yum/*

ENV LIBRARY_PATH /usr/local/cuda/lib64/stubs
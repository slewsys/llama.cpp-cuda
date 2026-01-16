# Makefile.am: Automake template for bash-dot-files.
#
# Process this file with automake to create Makefile.in
#
BUILD_DIR := $(dir $(realpath $(lastword $(MAKEFILE_LIST))))

bin_SCRIPTS = install-llama.cpp-cuda
EXTRA_DIST = build-llama.cpp-cuda.in \
	     install-asdf.in \
	     install-intel-oneapi-hpc.in \
	     install-llama.cpp-cuda.in \
	     install-nvidia-cuda.in

AM_DEFAULT_SOURCE_EXT = .in

.PHONY: all clean-local


all: llama.cpp-cuda

llama.cpp-cuda: build-llama.cpp-cuda
	$(BUILD_DIR)build-llama.cpp-cuda $(abs_srcdir)

install: install-exec-local

install-exec-local: install-llama.cpp-cuda
	$(BUILD_DIR)install-llama.cpp-cuda

clean:
	rm -rf llama.cpp

build-llama.cpp-cuda: $(top_srcdir)/build-llama.cpp-cuda.in

install-asdf: $(top_srcdir)/install-asdf.in

install-llama.cpp-cuda: $(top_srcdir)/install-llama.cpp-cuda.in

install-intel-oneapi-hpc: $(top_srcdir)/install-intel-oneapi-hpc.in

install-nvidia-cuda: $(top_srcdir)/install-nvidia-cuda.in

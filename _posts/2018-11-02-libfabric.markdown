---
layout: post
title:  "Libfabric plugin for Mercury"
date:   2018-11-02 17:21:15
categories: documentation
---

## Introduction

This document assumes that the reader already has knowledge of Mercury and its
layers (NA / HG / HG Bulk).

## Requirements

## OFI Plugin Architecture

## Feature Matrix

Feature | tcp | verbs | psm2 | gni
--------|-----|-------|------|-------------
Source Addressing | :heavy_exclamation_mark: | :heavy_exclamation_mark: | :heavy_check_mark: | :heavy_check_mark:
Manual Progress | :heavy_exclamation_mark: | :heavy_check_mark: | :heavy_exclamation_mark: | :heavy_exclamation_mark:
`FI_WAIT_FD` | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_exclamation_mark:
Scalable Endpoints | :heavy_check_mark: | :x: | :heavy_check_mark: | :heavy_check_mark:


## Performance

Below is a performance comparison of the libfabric plugin  with available libfabric providers when using both
wait and busy spin mechanisms, mercury v1.0.0 and libfabric v1.7.0a1.

<hr/>
### InfiniBand `verbs;rxm`

Performance is measured between two nodes on ALCF's [cooley](https://www.alcf.anl.gov/user-guides/cooley) cluster using the FDR InfiniBand interface `mlx5_0`.
The following plot shows the RPC average time
compared to `ofi+tcp` when using one single RPC in-flight:

<figure>
  <img src="/assets/ofi_verbs/rpc_time1.svg" alt="RPC time 1" width="80%">
</figure>

Same plot but with 16 RPCs in-flight:

<figure>
  <img src="/assets/ofi_verbs/rpc_time16.svg" alt="RPC time 16" width="80%">
</figure>

The following plot shows the RPC with *pull* bulk transfer performance
compared to `ofi+tcp` with various transfer sizes:

<figure>
  <img src="/assets/ofi_verbs/write_bw1.svg" alt="Write Bandwidth 1" width="80%">
</figure>

Same plot but with 16 RPCs in-flight:

<figure>
  <img src="/assets/ofi_verbs/write_bw16.svg" alt="Write Bandwidth 16" width="80%">
</figure>

The following plot shows the RPC with *push* bulk transfer performance
compared to `ofi+tcp` with various transfer sizes:

<figure>
  <img src="/assets/ofi_verbs/read_bw1.svg" alt="Read Bandwidth 1" width="80%">
</figure>

Same plot but with 16 RPCs in-flight:

<figure>
  <img src="/assets/ofi_verbs/read_bw16.svg" alt="Write Bandwidth 16" width="80%">
</figure>

<hr/>
### Omni-Path `psm2`

Performance is measured between two nodes on LCRC's [bebop](https://www.lcrc.anl.gov/systems/resources/bebop/) cluster using the Omni-Path interface with PSM2 v11.2.23.
The following plot shows the RPC average time
compared to `ofi+tcp` when using one single RPC in-flight:

<figure>
  <img src="/assets/ofi_psm2/rpc_time1.svg" alt="RPC time 1" width="80%">
</figure>

Same plot but with 16 RPCs in-flight:

<figure>
  <img src="/assets/ofi_psm2/rpc_time16.svg" alt="RPC time 16" width="80%">
</figure>

The following plot shows the RPC with *pull* bulk transfer performance
compared to `ofi+tcp` with various transfer sizes:

<figure>
  <img src="/assets/ofi_psm2/write_bw1.svg" alt="Write Bandwidth 1" width="80%">
</figure>

Same plot but with 16 RPCs in-flight:

<figure>
  <img src="/assets/ofi_psm2/write_bw16.svg" alt="Write Bandwidth 16" width="80%">
</figure>

The following plot shows the RPC with *push* bulk transfer performance
compared to `ofi+tcp` with various transfer sizes:

<figure>
  <img src="/assets/ofi_psm2/read_bw1.svg" alt="Read Bandwidth 1" width="80%">
</figure>

Same plot but with 16 RPCs in-flight:

<figure>
  <img src="/assets/ofi_psm2/read_bw16.svg" alt="Write Bandwidth 16" width="80%">
</figure>

<hr/>
### Aries `gni`

Performance is measured between two Haswell nodes on Nersc's [cori](http://www.nersc.gov/users/computational-systems/cori/) system using the interface `ipogif0` with uGNI v6.0.14.0.
The following plot shows the RPC average time
compared to `ofi+tcp` when using one single RPC in-flight:

<figure>
  <img src="/assets/ofi_gni/rpc_time1.svg" alt="RPC time 1" width="80%">
</figure>

Same plot but with 16 RPCs in-flight:

<figure>
  <img src="/assets/ofi_gni/rpc_time16.svg" alt="RPC time 16" width="80%">
</figure>

The following plot shows the RPC with *pull* bulk transfer performance
compared to `ofi+tcp` with various transfer sizes:

<figure>
  <img src="/assets/ofi_gni/write_bw1.svg" alt="Write Bandwidth 1" width="80%">
</figure>

Same plot but with 16 RPCs in-flight:

<figure>
  <img src="/assets/ofi_gni/write_bw16.svg" alt="Write Bandwidth 16" width="80%">
</figure>

The following plot shows the RPC with *push* bulk transfer performance
compared to `ofi+tcp` with various transfer sizes:

<figure>
  <img src="/assets/ofi_gni/read_bw1.svg" alt="Read Bandwidth 1" width="80%">
</figure>

Same plot but with 16 RPCs in-flight:

<figure>
  <img src="/assets/ofi_gni/read_bw16.svg" alt="Write Bandwidth 16" width="80%">
</figure>
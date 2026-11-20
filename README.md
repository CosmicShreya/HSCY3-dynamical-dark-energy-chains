# MCMC chains: Probing Dynamical Dark Energy with HSC Year 3 Cosmic Shear

This repository contains the MCMC chains used in

> S. Mukherjee and S. More, "Probing Dynamical Dark Energy with Hyper
> Suprime-Cam Year 3 Cosmic Shear" (2026), arXiv:[to be added].

The chains constrain the wCDM and w0waCDM cosmological models using the
Hyper Suprime-Cam Year 3 (HSC-Y3) real-space cosmic shear two-point
correlation functions, alone and in combination with external
background-distance probes.

## Chain format

All chains were produced with CosmoSIS using the PolyChord nested sampler.
Each file is a standard CosmoSIS text output:

- The header lines (starting with `#`) list the column names and record the
  full pipeline configuration (module list and all settings) used for the run.
- Each subsequent row is one sample.
- The `weight` column gives the sample weight and must be used when
  computing posteriors.

Example (Python):

    import numpy as np
    with open("chains/wCDM/wCDM_HSCY3.txt") as f:
        names = f.readline().lstrip("#").split()
    data = np.loadtxt("chains/wCDM/wCDM_HSCY3.txt")
    weights = data[:, names.index("weight")]

## Naming convention

| Tag          | Meaning                                                         |
|--------------|-----------------------------------------------------------------|
| `HSCY3`      | HSC-Y3 real-space cosmic shear (xi+ and xi-)                    |
| `DESIDR2`    | DESI DR2 BAO                                                    |
| `DESDovekie` | DES-Dovekie Type Ia supernovae (fiducial SN sample)             |
| `DESY5SN`    | DES Y5 Type Ia supernovae (used only for the DES Y5 comparison) |
| `BBN`        | Big Bang Nucleosynthesis prior on omega_b                       |
| `DESIzprior` | DESI cross-correlation priors on the photo-z shifts             |
| `drop_zbinN` | Tomographic bin N removed from the HSC-Y3 data vector           |

## Files and corresponding figures

### wCDM (`chains/wCDM/`)

| File | Figure(s) in paper |
|------|--------------------|
| `wCDM_HSCY3.txt` | 2, 3, 4, 11 |
| `wCDM_HSCY3_DESIDR2_DESDovekie_BBN.txt` | 2, 3, 4, 8, 11 |
| `wCDM_HSCY3_DESIDR2_DESDovekie_BBN_DESIzprior.txt` | 4 |
| `wCDM_HSCY3_DESIDR2_DESY5SN_BBN.txt` | 6 |
| `wCDM_HSCY3_DESIDR2_DESDovekie_BBN_drop_zbin1.txt` | 8 |
| `wCDM_HSCY3_DESIDR2_DESDovekie_BBN_drop_zbin2.txt` | 8 |
| `wCDM_HSCY3_DESIDR2_DESDovekie_BBN_drop_zbin3.txt` | 8 |
| `wCDM_HSCY3_DESIDR2_DESDovekie_BBN_drop_zbin4.txt` | 8 |

### w0waCDM (`chains/w0waCDM/`)

| File | Figure(s) in paper |
|------|--------------------|
| `w0waCDM_HSCY3.txt` | 5, 12 |
| `w0waCDM_HSCY3_DESIDR2_DESDovekie_BBN.txt` | 5, 8, 12 |
| `w0waCDM_HSCY3_DESIDR2_DESY5SN_BBN.txt` | 7 |
| `w0waCDM_HSCY3_DESIDR2_DESDovekie_BBN_drop_zbin1.txt` | 8 |
| `w0waCDM_HSCY3_DESIDR2_DESDovekie_BBN_drop_zbin2.txt` | 8 |
| `w0waCDM_HSCY3_DESIDR2_DESDovekie_BBN_drop_zbin3.txt` | 8 |
| `w0waCDM_HSCY3_DESIDR2_DESDovekie_BBN_drop_zbin4.txt` | 8 |

## Note on the linear matter power spectrum

For the wCDM chains, the linear matter power spectrum is computed with the
BACCO linear emulator (CosmoSIS module `pklin`); CAMB is also run in this
pipeline, but the BACCO spectrum is the one used downstream.
For the w0waCDM chains, the BACCO module was removed and the linear matter
power spectrum is computed with the Einstein-Boltzmann code CAMB. All other
pipeline modules and settings are identical. The complete configuration
for each run is recorded in the header of the corresponding chain file.

## External chains (not included)

The following chains appear in the paper's figures but were produced by
other groups and are not redistributed here:

- HSC-Y3 + SDSS 3x2pt (Zhang et al. 2025), shown in Figs. 3 and 4.
- DES Y5 3x2pt + SN + eBOSS, shown in Figs. 6 and 7, available from the
  public DES-SN5YR data release.

## Citation

If you use these chains, please cite the paper above.

## Contact

Shreya Mukherjee: shreya.mukherjee@iucaa.in

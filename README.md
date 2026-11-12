# Physical Execution Boundary

**Hardware Enforcement at the Physical Execution Boundary**  
Jungsoo Baek · Certum Systems · [ORCID](https://orcid.org/0009-0004-6648-0809)

A compromised controller can send well-formed commands through an interface it is allowed to use. This note examines where to enforce limits between that controller and the actuators, and how to check whether the host can alter or bypass them.

**[Read the paper on Zenodo](https://doi.org/10.5281/zenodo.24163561)** · [English PDF](https://zenodo.org/records/24163561/files/Physical_Execution_Boundary_EN.pdf?download=1) · [한국어 PDF](https://zenodo.org/records/24163561/files/Physical_Execution_Boundary_KO.pdf?download=1)

Version 1.0 · November 12, 2026 · Six pages in each language

## What the paper covers

The reference architecture separates three decisions:

- **Formation:** a verified execution permit determines which electrical paths may be formed.
- **Authority:** the host cannot electrically drive the final path-selection input, including through an alternate driver or interface.
- **Energy:** a safety monitor independent of host software supplies approval and operating limits. Without approval, the output stage holds a protected default that host software cannot change at runtime. With approval, it applies the lower of the evaluated limit and a hardware ceiling that the host cannot raise during normal operation.

Section 5 describes how the three combine, including what happens when permission or approval is withdrawn.

## Checks for an implementation

Section 6 sets out the assessment work:

- Measure path state independently of host reports. Invalid or absent permission must leave the controlled paths open.
- Trace every driver of the final selection input, including multiplexers, reset, debug and test interfaces.
- Measure the default and approved electrical limits. Repeat after weakening host-accessible access control.
- Measure withdrawal timing and exercise startup, recovery and mismatched approvals, and report shared dependencies.

The October 2026 RTL reference has simulation, synthesis and FPGA place-and-route results. Formal checks use a control model with an abstracted authentication response. Hardware evaluation, including tests with adversarial host firmware and electrical measurements, is the next step.

## Citation

Baek, J. (2026). *Hardware Enforcement at the Physical Execution Boundary* (Version 1.0). Zenodo. https://doi.org/10.5281/zenodo.24163561

The repository's **Cite this repository** entry points to the paper. [CITATION.cff](CITATION.cff) contains the citation metadata.

## License

The paper and this documentation are available under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

Implementations of the principles described here may be covered by patents and patent applications held by Certum Systems. This document grants no patent license.

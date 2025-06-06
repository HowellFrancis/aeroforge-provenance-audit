# BrewHaul Provenance Audit: Aerospace Chain of Custody Simulation
## Executive Summary
This repository documents a smart contract vulnerability simulation conducted by BrewHaul USA, modeling a scenario where a Tier 2 aerospace supplier accepts forged titanium certification records into its blockchain-based component provenance system. The project exposes a vulnerability in poorly validated Certificate of Authenticity (CoA) submissions, simulating a spoof that evades 3PL integration safeguards and could lead to material risk in final assemblies at Boeing and Airbus.
##Objectives
1. Deploy a vulnerable provenance ledger contract
2. Simulate a forged CoA injection
3. Demonstrate exploit feasibility
4. Patch the vulnerability and validate remediation
5. Publish a redacted public disclosure

## Project Structure  
  - 'contracts/' - 'VulnProvenance.sol' vulnerable contract, 'HardenedProvenance.sol' - patched version
  - 'exploit/' - proof-of-concept attack scripts
  - 'scripts/' - deployment and testing automation
  - 'tests/' - test harness for regression validation
  - 'docs/' - design docs, STRIDE model, patch rationale  
  - 'README.md' - this file  
  
## Threat Model Summary (STRIDE)  
|  Threat  |  Example  |  Control (Pre-Patch)  |  Control (Post-Patch)  |  
|  Spoofing  |  Fake CoA hash accepted  |  None  | Signature verification  |  
|  Tampering  | Metadata hash mismatch  | None  | Immutable timestamp, merkle root validation  |  
|  Repudiation  | Overwriting CoAs  |  Unlogged  |  Emit event logs  |  
|  Info Disclosure  |  CoA hash leak  |  Public  |  Optional hash salt  |  
|  Denial of Service  | Flood contract with fake CoAs  |  None  | Submisison rate limiting |  
|  Elevation of Privilege |  Any address can submit  | Open  | Restrict to known vendor wallet list |  
  
## Technologies  
  - AWS CloudShell EDE
  - Solidity / Foundry  
  - Sepolia testnet (Alchemy RPS)  
  - Markdown + GitHub Pages (docs)  
  - Custom threat model and private bug bounty disclosure  
  
---  
##License  
MIT  

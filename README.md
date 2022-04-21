# ads-ael-expressions
Collection of AEL measurement expressions for ADS data display

# Expressions

## cw_evm_estimateion
The permute statements in the defintiions of NormGain and NormPhase are needed in order to work with multidimensional sweeps.  These are the needed DDS equations in order for it to work.

Pavs = Source Power (dBm)
Pload = Delivered power (dBm)
Pstep = Power sweep step size (dBm)
GT = Pload - Pavs
NormGain=permute(permute(GT) - permute(GT[0]))
NormPhase=permute(permute(unwrap(phase(Vload))) - permute(unwrap(phase(Vload[0]))))
EVM = cwevm(Pavs, Pload, NormGain, NormPhase, Pstep, -30, 10)
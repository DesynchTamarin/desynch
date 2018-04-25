# Desynch

This repository contains the Tamarin implementations of several security protocols analysed as part of the Esorics 2018 submission on Desynchronisation Resistance of Key-Updating Protocols.

## Organisation

Individual protocols are split into separate folders. Each folder contains a .spthy file for the Tamarin implementation. In addition, you will find .pdf files containing the intended protocol execution an attack trace on the relevant protocol. For full information about the protocols, it is strongly recommended to read the original papers.

The .spthy files should contain sufficient annotation to make the implementation clear.

## Execution

Assuming the Tamarin prover tool has been installed, the most straightforwards means of execution is through the command

tamarin-prover --prove <filename>
  
 which will automatically prove all of the lemmas in the target file. Note that the lemmas in the source files consist of more than just the security claims made in the original paper. They can be roughly categorised into three sorts:
 
 * 'Check' lemmas, which verify that the protocol is executable and there and there are valid traces. Without these we cannot be certain that claims over 'all traces' are not trivially true (because there are no significant traces)
 * 'Helper' lemmas, which aid Tamarin in automating the proof process. Tamarin uses induction proofs to verify claims over stateful protocols with facts that can be infinitely updated. However, in some cases it is necessary to give it a point in the right direction.
 * 'Security' lemmas, which actually validate the desired security properties

# Branch_Predictor
The attached files are the asm generation files for testing of branch predictor and work in the [chromite_uatg_tests](https://github.com/incoresemi/chromite_uatg_tests) as a submodule under the BPU. We have used the demo codes provided here as templates for our codes.

## Code Description
#### uatg_fa_gshare_bht.py 
- tries to fill bht completely, more work is required to guarantee it access all values, the hash function is not explicilty mentioned and the assumption to use EXOR doesnt work since we require a 9 bit index as a result of the PC and History registers, and also dependent on the starting state of the 2-bit model.
#### uatg_gshare_fa_bht_fence_postfull.py
- fills the BTB and then flushes it using a fence instruction.
#### uatg_gshare_fa_bht_rollback_postfull.py
- fills the history registers with while adding confidence to a pariticular branch in the BHT, then it simulates an incorrect branch, which forces the history reg to rollback and the BHT to drop in confidence.
#### uatg_gshare_fa_btb_fill_02.py
- fills the btb share just like the demo code in the repo mentioned above but with compressed intructions. We have retained t1, t2 from the ABI assumining no change in the naming.
#### uatg_gshare_fa_ghr_alternating_compressed.py 
- fills ghr with alternating ones and zeros using compressed branch instruction.
#### uatg_gshare_fa_ras_push_pop_overload.py 
- overflows the ghr with more number of calls than the size and tries to return. 

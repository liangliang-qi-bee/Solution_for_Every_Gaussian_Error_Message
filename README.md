# Solutions for Gaussian Error Messages (migration work in progress :hourglass_flowing_sand:)
This is an article containing reliable explanations and ways to solve the error messages for almost all common Gaussian quantum chemistry programs. This is a per request English translation for [a long blog in Chinese](http://bbs.keinsci.com/thread-4829-1-1.html) I wrote a few years back. I wrote the original Chinese post as there is almost no reliable list of how to solve the errors. Similar online resources online are neither comprehensive nor accurate.

This blog is for people with basic knowledge of how Gaussian works, what's the basic structure of Gaussian files, and a basic understanding of quantum chemistry.

Using (including part of) this blog in a commercial setting (or for any profitable action) is prohibited. Otherwise, feel free to use this material as long as you mention the source.

I'm not related to Gaussian Inc. in any way.

## List of errors
### General errors
 * [Severe Error Message # 2070 (Windows)](#SevereErrorMessage2070)
 * [segmentation violation/segmentation fault (Linux)](#SevereErrorMessage2070)
### Errors raised by specific links
 * [**L1**，ntrex1](#1200)
 * [**L1**，Illegal IType or MSType generated by parse.](#1100)
 * [**L1**，QPErr --- A syntax error was detected in the input line.](#1300)
 * [**L101**，End of file in ZSymb.](#700)
 * [**L101**，WANTED A XXX AS INPUT. FOUND AN XXX AS INPUT.](#800)
 * [**L101**，Input Error Input Error Input Error Input Error Input Error Input Error](#900)
 * [**L103**，Error in internal coordinate system](#600)
 * [**L103**，Linear angle in Bend; Linear angle in Tors](#600)
 * [**L103**，FormBX had a problem](#600)
 * [**L103**，NRF ne Abs NRFX](#2500)
 * [**L103**，New curvilinear step not converged. Error imposing constraints.](#2300)
 * [**L103**，Bad arguments to LAPack or BLAS routine.](#3700)
 * [**L114**，ERROR IN INITNF. NUMBER OF VARIABLES (  0) INCORRECT (SHOULD BE BETWEEN 1 AND 50)](#1800)
 * [**L123**，Max corrector steps exceded](#500)
 * [**L123**，GS2 Optimization Failure.](#500)
 * [**L123**，GetHes: LRWHes > LHess!](#2600)
 * [**L202**，Problem with the distance matrix.](#1000)
 * [**L202**，Atoms too close.](#1000)
 * [**L301**，The combination of multiplicity X and XXX electrons is impossible.](#1500)
 * [**L301**，End of file reading basis center.](#700)
 * [**L301**，EOF while reading ECP pointer card.](#700)
 * [**L301**，No solvent atoms in DisRep.](#2400)
 * [**L301**，Atomic number out of range for XXX basis set.](#1400)
 * [**L301**，R6DS8: Unable to choose the S8 parameter](#1600)
 * [**L301**，R6DRCv: No RCov radius available for IA=XX](#1700)
 * [**L301**，R6DC6: No C6 coefficient available for IA=XX](#1700)
 * [**L401**，Diagonalization in DiagDN via DSPEV failed.](#3700)
 * [**L502**，Convergence failure](#100)
 * [**L502**，Inaccurate quadrature in CalDSu.](#300)
 * [**L502**，Inv3 failed in PCMMkU](#2100)
 * [**L508**，Convergence failure](#200)
 * [**L508**，Inv3 failed in PCMMkU](#2100)
 * [**L602**，GetVDW:  no radius for atom XX atomic number XX.](#2800)
 * [**L801**，Excessive mixing of core and valence orbitals.](#1900)
 * [**L801**, Fatal Problem: The smallest alpha delta epsilon is XXXXXX](#2000)
 * [**L906**，Internal consistency failure #1 in GetIJB.](#3700)
 * [**L913**，\*MAX. CYCLES\*](#2200)
 * [**L914**，XXXXXX words are not enough for AIAXAO.](#3400)
 * [**L914**，Unable to match L and R vectors in BiOrth](#3700)
 * [**L1002**，Inaccurate quadrature in CalDSu.](#300)
 * [**L1002**，No func 3rd derivs with XXX.](#2700)
 * [**L1002**，NIJ > Max2 in MMCore.](#3700)
 * [**L1002**，XXXXXX words are not enough for AIAXAO.](#3400)
 * [**L1014**，Tx not orthogonal to T](#3700)
 * [**L9999**，Optimization stopped.](#400)
### Computer/OS related errors
#### CPU
 * [Error: illegal instruction, illegal opcode](#2900)
#### File
 * [Internal input file was deleted!](#3000)
 * [open-new-file](#3100)
 * [Error Message # 2066. Can't create file Temp input file 'gxx.inp'](#3200)
#### Hard drive
 * [Erroneous write](#3300)
 * [g_write](#3300)
#### Memory
 * [needs more words of memory](#3400)
 * [Not enough memory to run at all](#3400)
 * [Out-of-memory error in routine XXX](#3400)
 * [galloc:  could not allocate memory.](#3500)
### Difficult cases
 * [NtrErr Called from XXXXXX.](#3600)
### What does a Gaussian Bug look like
 * [Is it a bug?](#3700)
### Abnormal situations that don't give an error message
 * [IRC job stopped prematurely, or goes in another direction](#3800)
 * [One or more small imaginary frequencies after optimization](#3900)
 * [G09 Windows exit at L1.exe without an error message](#4000)
 * [Abnormal bonding / unbonding in GaussView](#4100)
 * [Viewing IRC jobs in GaussView, it gives an abnormally low energy point at the X=0 point](#4200)
### Normal outputs that could be mistaken as errors
 * [Warning!!: The largest alpha MO coefficient is...](#4800)
 * [Warning!!: The smallest alpha delta epsilon is...](#4800)
 * [Error on total polarization charges](#4900)
 * [This type of calculation cannot be archived.](#5000)
 * [No special actions if energy rises.](#5100)
 * [DIIS: error](#5200)
 * [End of XXXXXX F.D. properties file   XXX does not exist.](#5300)
### Other common questions
 * ["Missing or bad data: Alpha Orbital Energies" when opening chk or fchk files with GaussView](#4300)
 * [“How long will this calculation takes?”](#4400)
 * [How to generate an initial guess for transition state geometry optimization with flexible scan](#4500)
 * [“How to put a charge / electron on this atom / fragment?"](#4600)
 * [How to calculate activation-strain (distortion-interaction) energy](#4700)

## Explanation and solution for the errors
For ones who would like to read this in whole, the order of the following sections is different from the [list of errors](#List-of-errors) above. Use the anchor links if you would like to navigate to specific errors.

### General errors
<a name="SevereErrorMessage2070"></a>
####  :arrow_forward: Severe Error Message # 2070 (Windows) 
####  :arrow_forward: segmentation violation/segmentation fault (Linux) 

**· Example:**


Linux

    Error: segmentation violation
       rax 0000000000000000, rbx 000000000060c640, rcx ffffffffffffffff
       rdx 0000000000007f57, rsp 0000007fbffed948, rbp 0000007fbffed970
       rsi 000000000000000b, rdi 0000000000007f57, r8  0000002a9558af40
       r9  0000000000000000, r10 0000007fbffed801, r11 0000000000000206
       r12 0000000000615890, r13 0000000000640398, r14 0000000000640398
       r15 0000000000640398
       
Windows

<p align="center"><img src="https://user-images.githubusercontent.com/18537705/134765617-ca4a7f87-8fb0-4c83-93e1-e4c1deac7418.png" width="80%" height="80%" align="center"></img></p>

**· Explanation**

This is just a message saying "Something is wrong" without any specific information. 

**· Solution**

As there is no info on the specific error, any method you got online for _"how to solve the Gaussian 2070 error"_ is nonsense. You should look at the (end of the) output file to see the specific reason for the error.

On the windows version of the Gaussian, the output might not update when the error happened, so you might see an empty window. In this case, you need to open the output file itself or wait some time to see the text in the main UI.

#
### SCF Convergence
<a name="100"></a>
####  · L502，Convergence failure :hourglass_flowing_sand:

**· Example:**


     Cycle 128  Pass 1  IDiag  1:
     RMSU=  9.02D-07    CP:  1.00D+00  9.48D-01  3.00D+00  1.61D+00  1.30D+00
                        CP:  1.61D+00  1.46D+00
     E= -14914.8006510842     Delta-E=        0.000260457560 Rises=F Damp=F
     DIIS: error= 1.39D-02 at cycle 128 NSaved=  20.
     NSaved=20 IEnMin=16 EnMin= -14923.1431281454     IErMin= 8 ErrMin= 8.37D-03
     ErrMax= 1.39D-02  0.00D+00 EMaxC= 1.00D-01 BMatC= 8.92D-01 BMatP= 4.53D-01
     IDIUse=2 WtCom= 0.00D+00 WtEn= 1.00D+00
     EnCoef did    94 forward-backward iterations
     Coeff-En:   0.837D-01 0.000D+00 0.544D-01 0.287D+00 0.818D-03 0.000D+00
     Coeff-En:   0.000D+00 0.000D+00 0.149D+00 0.485D-05 0.228D-01 0.144D-03
     Coeff-En:   0.903D-02 0.129D-03 0.778D-04 0.393D+00 0.216D-03 0.313D-03
     Coeff-En:   0.237D-03 0.376D-03
     Coeff:      0.837D-01 0.000D+00 0.544D-01 0.287D+00 0.818D-03 0.000D+00
     Coeff:      0.000D+00 0.000D+00 0.149D+00 0.485D-05 0.228D-01 0.144D-03
     Coeff:      0.903D-02 0.129D-03 0.778D-04 0.393D+00 0.216D-03 0.313D-03
     Coeff:      0.237D-03 0.376D-03
     Gap=     0.015 Goal=   None    Shift=    0.000
     RMSDP=1.87D-06 MaxDP=3.06D-04 DE= 2.60D-04 OVMax= 8.02D-05

     >>>>>>>>>> Convergence criterion not met.
     Error on total polarization charges = ********
     SCF Done:  E(RPBE1PBE) =  -14914.8006511     A.U. after  129 cycles
                NFock=128  Conv=0.19D-05     -V/T= 4.2204
     KE= 4.631417055578D+03 PE=-4.911726716823D+04 EE= 7.213578297303D+03
     SMD-CDS (non-electrostatic) energy       (kcal/mol) =      -6.81
     (included in total energy above)
     Convergence failure -- run terminated.
     Error termination via Lnk1e in /gpfs/share/home/1501110295/g16/l502.exe at Tue Mar 31 23:16:51 2020.
     Job cpu time:       7 days 18 hours 47 minutes 16.6 seconds.
     Elapsed time:       0 days  5 hours 57 minutes 42.6 seconds.
     File lengths (MBytes):  RWF=   3744 Int=      0 D2E=      0 Chk=    176 Scr=     32

**· Explanation**

This is one of the most common problems in daily operations. The SCF (self-consistent field) iteration is not converged to below the threshold you designated (scf=conv=XX, default 1D-8) within the maximum number of cycles (scf=maxcyc=XX, default 128 cycles) you designated.

**· Identify the problem**

Before finding solutions, you need to identify specifically how is the convergence going. To do this, you need to replace the `#` to `#p` in your route card to show details of SCF iteration (I suggest always doing this, except for special jobs like ONIOM with a large molecule). You can plot the `E = -XXX.XXXXX` in each cycle, zoom in to the graph so that the changes in the later cycles are clearly visible (referred to as "the curve" later). From the curve, you may find a few scenarios, and you should deal with each one of them separately:

1. **\[Fluctuation at initial stage\]**: The curve is fluctuating, and the convergence (given by `NFock=128  Conv=XXXXD-XX` in the output) is far from the threshold, usually larger than 10^-3 hartree). The fluctuation can be somewhat chaotic:

<p align="center"><img src="https://user-images.githubusercontent.com/18537705/134804057-5b071d62-cbfa-42f3-9876-b09b1b6b28d2.png" width="30%" height="30%"></img></p>

or can also be oscillating with a fixed period:

<p align="center"><img src="https://user-images.githubusercontent.com/18537705/134804352-bcb54e9f-80fe-4f51-807e-08d6a3f8a54e.png" width="30%" height="30%" align="center"></img></p>

(please ignore the vertical axis, this is an output of my `QM Monitor` program, and the vertical axis does not linearly correspond to energy.)

2. **\[Fluctuation at later stage\]**: same with above, just the convergence is closer to the threshold, like 10^-5 hartree or below

3. **\[Monotonous decline\]**: The curve is monotonously declining (it's ok to have a few points as exceptions to the monotonous trend), but doesn't converge at maxcyc. This situation is exceedingly rare. I believe I've only encountered this less than 5 times in all my calculations, and interestingly, several of them involves lanthanide atoms. 

<p align="center"><img src="https://user-images.githubusercontent.com/18537705/134804908-2b72744f-0fc7-42d6-9bed-22692adbbf54.png" width="30%" height="30%" align="center"></img></p>

4. **\[SCF (curve shape irrelevant) with drastically different electronic energy for similar structures\]** (for example, during optimization). For example, the image and output below represent a job that ends with an SCF convergent failure. The last step has an SCF energy several hundred hartree higher than previous ones. Reviewing the optimization process (Image below, right), you can see the optimization kinda goes haywire (the forces and displacements don't look right) at around step 39. which is reflexed in the jump of his SCF energy (despite it has converged). Steps 50 and 56 (highlighted with arrow) also have energy tens of hartrees above the normal ones. This usually indicated a deeper problem than just SCF convergence problem and could be raised from dividing a very small number and results in a very large numerical error. The small number could be caused by the linear dependency of the basis sets or solvation cavity problems (see the section [L502/L508，Inv3 failed in PCMMkU](#2100)).

<p align="center"><img src="https://user-images.githubusercontent.com/18537705/134805076-4bfd9d2b-b85c-41a8-b43f-641ca2e593e7.png" width="50%" height="50%" align="center"></img></p>

    Opt Step 37:  SCF Done:  E(RB-P86) =  -3825.13282335     A.U. after   12 cycles
    Opt Step 38:  SCF Done:  E(RB-P86) =  -3825.13719799     A.U. after   11 cycles
    --> Opt Step 39:  SCF Done:  E(RB-P86) =  -3825.10522704     A.U. after   13 cycles
    Opt Step 40:  SCF Done:  E(RB-P86) =  -3825.13602726     A.U. after   12 cycles
    Opt Step 41:  SCF Done:  E(RB-P86) =  -3825.13709759     A.U. after    8 cycles
    Opt Step 42:  SCF Done:  E(RB-P86) =  -3825.13718461     A.U. after    7 cycles
    Opt Step 43:  SCF Done:  E(RB-P86) =  -3825.13719706     A.U. after    1 cycles
    Opt Step 44:  SCF Done:  E(RB-P86) =  -3825.13719791     A.U. after    1 cycles
    Opt Step 45:  SCF Done:  E(RB-P86) =  -3825.13222362     A.U. after   12 cycles
    Opt Step 46:  SCF Done:  E(RB-P86) =  -3825.13968083     A.U. after   12 cycles
    Opt Step 47:  SCF Done:  E(RB-P86) =  -3825.13599635     A.U. after   13 cycles
    Opt Step 48:  SCF Done:  E(RB-P86) =  -3825.13662431     A.U. after   12 cycles
    Opt Step 49:  SCF Done:  E(RB-P86) =  -3825.13636208     A.U. after   12 cycles
    --> Opt Step 50:  SCF Done:  E(RB-P86) =  -3845.72449495     A.U. after   54 cycles
    Opt Step 51:  SCF Done:  E(RB-P86) =  -3825.13665330     A.U. after   20 cycles
    Opt Step 52:  SCF Done:  E(RB-P86) =  -3825.13647203     A.U. after   23 cycles
    Opt Step 53:  SCF Done:  E(RB-P86) =  -3825.13594059     A.U. after   26 cycles
    Opt Step 54:  SCF Done:  E(RB-P86) =  -3825.13482223     A.U. after   26 cycles
    Opt Step 55:  SCF Done:  E(RB-P86) =  -3825.13408631     A.U. after   35 cycles
    --> Opt Step 56:  SCF Done:  E(RB-P86) =  -3888.91182114     A.U. after   73 cycles
    Opt Step 57:  SCF Done:  E(RB-P86) =  -3825.13665328     A.U. after   22 cycles
    Opt Step 58:  SCF Done:  E(RB-P86) =  -3825.13647358     A.U. after   25 cycles
    Opt Step 59:  SCF Done:  E(RB-P86) =  -3825.13595614     A.U. after   26 cycles
    Opt Step 60:  SCF Done:  E(RB-P86) =  -3825.13490799     A.U. after   27 cycles
    Opt Step 61:  SCF Done:  E(RB-P86) =  -3825.13382018     A.U. after   30 cycles
    --> Opt Step 62:  SCF Done:  E(RB-P86) =  -4207.17296836     A.U. after  129 cycles
    
**· Solution**:hourglass_flowing_sand:

First of all, there is almost no keyword that can systematically increase the chance of convergence in everyday calculation. I suggest against adding any additional SCF-related keywords to your input file (i.e., keep it as the default).

(Many of the following content in this section referenced [this Chinese post](http://sobereva.com/61) by Sobereva.)

1. For **\[Monotonous decline\]** ONLY, use `scf=maxcyc=XX` (choose a number larger than 128) to increase the maximum number of cycles. As I mentioned before, this is a rare situation, and this keyword is heavily abused on the internet. Use this keyword in any other situations will only caused you unnecessary CPU times. And it is a sign of ignorance if you see someone write this option as his "default option" (i.e. write this to all the input files).

2. For **\[Fluctuation at initial stage\]**, first try one or a combination of several of the keywords below:
   - `SCF=NoVarAcc`: In L502 output, you can see this sentence `Initial convergence to 1.0D-05 achieved.  Increase integral accuracy.` (example below), which means before this step, as the SCF is far from convergent, Gaussian will use a lower integration accuracy to save time. However this may cause SCF fluctuation, in that case, disabling it may solve the problem. Adding this keyword will almost nevel cause a convergent SCF to become divergent, but it will likely cause an increase in the computation time. 
```
     Coeff:      0.113D+00 0.365D+00 0.534D+00
     Gap=     0.125 Goal=   None    Shift=    0.000
     RMSDP=9.29D-06 MaxDP=3.04D-03 DE=-3.18D-03 OVMax= 3.90D-03

     Cycle  10  Pass 0  IDiag  1:
     RMSU=  6.05D-06    CP:  9.87D-01  6.50D-01  1.65D-01  6.63D-02  6.41D-01
                        CP:  6.58D-01  7.67D-01  8.17D-01  7.24D-01
     E= -13297.5461801855     Delta-E=       -0.000664594365 Rises=F Damp=F
     DIIS: error= 2.05D-04 at cycle  10 NSaved=  10.
     NSaved=10 IEnMin=10 EnMin= -13297.5461801855     IErMin=10 ErrMin= 2.05D-04
     ErrMax= 2.05D-04  0.00D+00 EMaxC= 1.00D-01 BMatC= 1.37D-04 BMatP= 8.51D-04
     IDIUse=3 WtCom= 9.98D-01 WtEn= 2.05D-03
     Coeff-Com: -0.513D-03 0.181D-02-0.342D-02 0.137D-02-0.404D-02-0.120D-01
     Coeff-Com:  0.518D-02 0.669D-01 0.176D+00 0.769D+00
     Coeff-En:   0.000D+00 0.000D+00 0.000D+00 0.000D+00 0.000D+00 0.000D+00
     Coeff-En:   0.000D+00 0.000D+00 0.000D+00 0.100D+01
     Coeff:     -0.511D-03 0.180D-02-0.341D-02 0.137D-02-0.404D-02-0.120D-01
     Coeff:      0.517D-02 0.668D-01 0.176D+00 0.769D+00
     Gap=     0.123 Goal=   None    Shift=    0.000
     RMSDP=4.95D-06 MaxDP=6.20D-04 DE=-6.65D-04 OVMax= 1.54D-03

     --> Initial convergence to 1.0D-05 achieved.  Increase integral accuracy.
     Cycle  11  Pass 1  IDiag  1:
     E= -13297.5469692442     Delta-E=       -0.000789058700 Rises=F Damp=F
     DIIS: error= 2.66D-04 at cycle   1 NSaved=   1.
     NSaved= 1 IEnMin= 1 EnMin= -13297.5469692442     IErMin= 1 ErrMin= 2.66D-04
     ErrMax= 2.66D-04  0.00D+00 EMaxC= 1.00D-01 BMatC= 3.14D-04 BMatP= 3.14D-04
     IDIUse=3 WtCom= 9.97D-01 WtEn= 2.66D-03
     Coeff-Com:  0.100D+01
     Coeff-En:   0.100D+01
     Coeff:      0.100D+01
     Gap=     0.117 Goal=   None    Shift=    0.000
     RMSDP=4.95D-06 MaxDP=6.20D-04 DE=-7.89D-04 OVMax= 4.47D-03

     Cycle  12  Pass 1  IDiag  1:
     RMSU=  7.87D-05    CP:  1.00D+00
     E= -13297.5470667379     Delta-E=       -0.000097493670 Rises=F Damp=F
```

   - `SCF=NoIncFock`: Incremental Fock matrix build is an accelaration technique where the Fock matrix is computed recursively using the difference density of the last 2 SCF cycles. This could drastically lower the scaling of the Fock matrix build. However, this may cause fluctuation especially when diffuse functions are used. To solve this, use `SCF=NoIncFock` turns off incremental Fock matrix build. This will results in higher cost of each SCF cycle.

   - `IOp(5/37=N)`: By default, Gaussian will rebuild the Fock matrix in full for every 20 cycles of SCF iteration: `IOp(5/37)=20` by default. This is shown as `Fock matrices will be formed incrementally for  20 cycles.` and `Restarting incremental Fock formation.` in the Gaussian output (example of output below). You can select a N<20, and involke the IOp(5/37=N) option to form the fock matrix every N SCF cycles. The relashionship between `SCF=NoIncFock` and `IOp(5/37=N)` are similar to `opt=CalcAll` and `opt=Recalc=N`.

```
 Requested convergence on             energy=1.00D-06.
 No special actions if energy rises.
 --> Fock matrices will be formed incrementally for  20 cycles.

 Cycle   1  Pass 1  IDiag  1:
 FoFJK:  IHMeth= 1 ICntrl=       0 DoSepK=F KAlg= 0 I1Cent=           0 FoldK=F
 IRaf= 990000000 NMat=       1 IRICut=       1 DoRegI=T DoRafI=F ISym2E= 0 IDoP0=0 IntGTp=1.
 FoFCou: FMM=T IPFlag=           0 FMFlag=      100000 FMFlg1=        2001
 ...
 ...
 ...
 Coeff:     -0.634D-05 0.481D-03-0.104D-02 0.243D-02-0.167D-02 0.429D-02
 Coeff:      0.217D-02 0.976D-02-0.371D-01-0.324D-01 0.394D-02 0.132D+00
 Coeff:      0.254D+00 0.663D+00
 Gap=     0.029 Goal=   None    Shift=    0.000
 RMSDP=1.13D-03 MaxDP=7.30D-02 DE=-4.18D-04 OVMax= 1.76D-02

 Cycle  21  Pass 1  IDiag  1:
 --> Restarting incremental Fock formation.
 E= -1315.53915604307     Delta-E=       -0.000105907567 Rises=F Damp=F
 DIIS: error= 1.06D-04 at cycle  21 NSaved=  20.
 NSaved=20 IEnMin=20 EnMin= -1315.53915604307     IErMin=20 ErrMin= 1.06D-04
 ...
 ...
 ...
 Coeff:      0.627D-01 0.170D+00-0.268D+00-0.291D+00-0.212D+01 0.175D+01
 Coeff:     -0.254D+01 0.241D+01-0.587D+00 0.111D+01 0.166D+01-0.269D+01
 Coeff:     -0.561D+01 0.530D+01-0.209D+01 0.473D+01
 Gap=     0.052 Goal=   None    Shift=    0.000
 RMSDP=7.12D-04 MaxDP=8.59D-02 DE=-5.43D-03 OVMax= 4.24D-03

 Cycle  41  Pass 1  IDiag  1:
 --> Restarting incremental Fock formation.
 E= -5974.52121524936     Delta-E=       -0.000886211828 Rises=F Damp=F
 DIIS: error= 8.43D-03 at cycle  41 NSaved=  17.
 NSaved=17 IEnMin=11 EnMin= -5976.91129255226     IErMin=10 ErrMin= 6.51D-03
 ```


3. For **\[Fluctuation at later stage\]**:
   - `Int=UltraFine`: 【When it is useful】For methods that use a grid-based numerical integration (DFT only), insufficient grid quality could cause small numerical error that's just larger than the convergent threshold of SCF (and for the same reason, this is not likely to help flucturation at early stage of SCF). The [Minnesota functionals](https://en.wikipedia.org/wiki/Minnesota_functionals) are kinda notorious for their higher requirement for grid quality. Thus this is the prime recommendation if that is the case. I have examples where this keyword help with other functionals, but it's rarer than the Minnesota functionals. 【G16】Note that since Gaussian 16, the default option has already become `Int=Ultrafine`. So unless you specifically lowered it to `Int=Fine`, there is no need to write Int=Ultrafine explicitly. 【Comparablity】Energies at different integration grid is not comparable. If you raise the integration grid for one structure, you need to re-run all the calculations for which you are getting a difference in energy with that structure. One exception is that you can optimize the structure with Int=UltraFine grid, but do a Int=Find grid single point calculation to get the correct electronic energy, and add the later electronic energy with the thermodynamic correction at Int=UltraFine grid (This is because the intregration grid is not likely to greately affect the PES). You need to clearly state what integration grid you used in the Supporting Information of your publication (for repeatability). 【About SuperFine】There is a higher grid `Int=SuperFine`, however Int=UltraFine is usually good enough, and it is unlikely that SuperFine grid will solve SCF divergence, unless you are requiring some uncommon SCF threshold. 
4. 
5. Danger zone
   - `IOp(5/13=1)`: 
   
#
<a name="200"></a>
####  · L508，Convergence failure :hourglass_flowing_sand:
#
### Post-HF Convergence
<a name="2200"></a>
####  · L913，\*MAX. CYCLES\* :hourglass_flowing_sand:
#
### Geometry Optimization Convergence
<a name="400"></a>
####  · L9999，Optimization stopped. :hourglass_flowing_sand:
#
<a name="500"></a>
####  · L123，Max corrector steps exceded :hourglass_flowing_sand:
####  · L123，GS2 Optimization Failure. :hourglass_flowing_sand:
#
### Geometry Manipulation
<a name="600"></a>
####  · L103，Error in internal coordinate system :hourglass_flowing_sand:
####  · L103，Linear angle in Bend; Linear angle in Tors :hourglass_flowing_sand:
####  · L103，FormBX had a problem :hourglass_flowing_sand:
#
<a name="2300"></a>
####  · L103，New curvilinear step not converged. Error imposing constraints. :hourglass_flowing_sand:
#
### Nonsense Input File (Formatting / Structure / Route)
<a name="700"></a>
####  · L101，End of file in ZSymb. :hourglass_flowing_sand:
####  · L301，End of file reading basis center. :hourglass_flowing_sand:
####  · L301，EOF while reading ECP pointer card. :hourglass_flowing_sand:
#
<a name="800"></a>
####  · L101，WANTED A XXX AS INPUT. FOUND AN XXX AS INPUT. :hourglass_flowing_sand:
#
<a name="900"></a>
####  · L101，Input Error Input Error Input Error Input Error Input Error Input Error :hourglass_flowing_sand:
#
<a name="1100"></a>
####  · L1，Illegal IType or MSType generated by parse. :hourglass_flowing_sand:
#
<a name="1300"></a>
####  · L1，QPErr --- A syntax error was detected in the input line. :hourglass_flowing_sand:
#
<a name="1500"></a>
####  · L301，The combination of multiplicity X and XXX electrons is impossible. :hourglass_flowing_sand:
#
<a name="1000"></a>
####  · L202，Problem with the distance matrix. :hourglass_flowing_sand:
####  · L202，Atoms too close. :hourglass_flowing_sand:
#
<a name="1400"></a>
####  · L301，Atomic number out of range for XXX basis set. :hourglass_flowing_sand:
#
<a name="1600"></a>
####  · L301，R6DS8: Unable to choose the S8 parameter :hourglass_flowing_sand:
#
<a name="1700"></a>
####  · L301，R6DRCv: No RCov radius available for IA=XX :hourglass_flowing_sand:
####  · L301，R6DC6: No C6 coefficient available for IA=XX :hourglass_flowing_sand:
#
<a name="2400"></a>
####  · L301，No solvent atoms in DisRep. :hourglass_flowing_sand:
#
<a name="2800"></a>
####  · L602，GetVDW:  no radius for atom XX atomic number XX. :hourglass_flowing_sand:
#
<a name="2700"></a>
####  · L1002，No func 3rd derivs with XXX. :hourglass_flowing_sand:
#
<a name="2500"></a>
####  · L103，NRF ne Abs NRFX :hourglass_flowing_sand:
#
### Computer / OS Related Problems
<a name="2900"></a>
####  · Error: illegal instruction, illegal opcode :hourglass_flowing_sand:
#
<a name="3000"></a>
####  · Internal input file was deleted! :hourglass_flowing_sand:
#
<a name="3100"></a>
<a name="1200"></a>
####  · open-new-file :hourglass_flowing_sand:
####  · L1，ntrex1 :hourglass_flowing_sand:
#
<a name="3200"></a>
####  · Error Message # 2066. Can't create file Temp input file 'gxx.inp' :hourglass_flowing_sand:
#
<a name="3300"></a>
####  · Erroneous write :hourglass_flowing_sand:
####  · g_write :hourglass_flowing_sand:
#
<a name="3400"></a>
####  · L914，XXXXXX words are not enough for AIAXAO. :hourglass_flowing_sand:
####  · L1002，XXXXXX words are not enough for AIAXAO. :hourglass_flowing_sand:
####  · needs more words of memory :hourglass_flowing_sand:
####  · Not enough memory to run at all :hourglass_flowing_sand:
####  · Out-of-memory error in routine XXX :hourglass_flowing_sand:
#
<a name="3500"></a>
####  · galloc:  could not allocate memory. :hourglass_flowing_sand:
#
### Others
<a name="300"></a>
####  · L502/L1002，Inaccurate quadrature in CalDSu. :hourglass_flowing_sand:
#
<a name="1800"></a>
####  · L114，ERROR IN INITNF. NUMBER OF VARIABLES (  0) INCORRECT (SHOULD BE BETWEEN 1 AND 50) :hourglass_flowing_sand:
#
<a name="1900"></a>
####  · L801，Excessive mixing of core and valence orbitals. :hourglass_flowing_sand:
#
<a name="2000"></a>
####  · L801, Fatal Problem: The smallest alpha delta epsilon is XXXXXX :hourglass_flowing_sand:
#
<a name="2100"></a>
####  · L502/L508，Inv3 failed in PCMMkU :hourglass_flowing_sand:
#
<a name="2600"></a>
####  · L123，GetHes: LRWHes > LHess! :hourglass_flowing_sand:
#
<a name="3600"></a>
### Difficult cases
####  · NtrErr Called from XXXXXX. :hourglass_flowing_sand:
#
<a name="3700"></a>
### Probably known bugs
####  · What does a Gaussian Bug look like? :hourglass_flowing_sand:
Some known bugs:
 * L103，Bad arguments to LAPack or BLAS routine.
 * L401，Diagonalization in DiagDN via DSPEV failed.
 * L906，Internal consistency failure #1 in GetIJB.
 * L914，Unable to match L and R vectors in BiOrth
 * L1002，NIJ > Max2 in MMCore.
 * L1014，Tx not orthogonal to T
#
### Normal outputs that could be mistanken as errors :hourglass_flowing_sand:
<a name="4800"></a>
#### Warning!!: The largest alpha MO coefficient is... :hourglass_flowing_sand:
#### Warning!!: The smallest alpha delta epsilon is... :hourglass_flowing_sand:
#
<a name="4900"></a>
#### Error on total polarization charges :hourglass_flowing_sand:
#
<a name="5000"></a>
#### This type of calculation cannot be archived. :hourglass_flowing_sand:
#
<a name="5100"></a>
#### No special actions if energy rises. :hourglass_flowing_sand:
#
<a name="5200"></a>
#### DIIS: error :hourglass_flowing_sand:
#
<a name="5300"></a>
#### End of XXXXXX F.D. properties file   XXX does not exist. :hourglass_flowing_sand:
#
### Abnormal situations that doesn't give an error message


### Abnormal situations that don't give an error message
<a name="3800"></a>
####  · IRC job stopped prematurely, or goes in the other direction :hourglass_flowing_sand:
#
<a name="3900"></a>
####  · One or more small imaginary frequencies after optimization :hourglass_flowing_sand:
#
<a name="4000"></a>
####  · G09 Windows exit at L1.exe without an error message :hourglass_flowing_sand:
#
<a name="4100"></a>
####  · Abnormal bonding / unbonding in GaussView :hourglass_flowing_sand:
#
<a name="4200"></a>
####  · Viewing IRC jobs in GaussView, it gives an abnormally low energy point at the X=0 point :hourglass_flowing_sand:
#
<a name="4300"></a>
####  · "Missing or bad data: Alpha Orbital Energies" when opening chk or fchk files with GaussView :hourglass_flowing_sand:
#
### Other common entry-level questions 
<a name="4400"></a>
####  · “How long will this calculation takes?” :hourglass_flowing_sand:
#
<a name="4500"></a>
####  · How to generate an initial guess for transition state geometry optimization with flexible scan :hourglass_flowing_sand:
#
<a name="4600"></a>
####  · “How to put a charge / electron on this atom / fragment?" :hourglass_flowing_sand:
#
<a name="4700"></a>
####  · How to calculate activation-strain (distortion-interaction) energy :hourglass_flowing_sand:
#

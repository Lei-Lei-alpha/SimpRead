> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [mattermodeling.stackexchange.com](https://mattermodeling.stackexchange.com/questions/1176/calculating-hse06-band-structures-on-quantum-espresso)

> I am currently trying to figure out how to compute band structures for my system, using the hybrid fu......

I have seen all the methods you mentioned but have only done one myself; I'll explain here how to use Wannier90 in conjunction with Quantum Espresso to get band structures for hybrid functional calculations. It does take a bit of time to learn, but not very long! You can learn the basics and do some first calculations in an afternoon. There are subtleties of course that I won't get into, and if you have specific issues you should probably ask another question or send a message to the Wannier90 mailing list.

Initial Checklist
-----------------

1.  Compile and install [Wannier90](http://www.wannier.org/)
    
2.  If you are using QE <= 6.0, you will need to replace the qe/PP/src/pw2wannier90.f90 file with one provided in the Wannier90 tarball, and recompile QE. Otherwise, make sure you have a working compiled version of QE. Newer versions will typically be better for hybrid functional calculations (pairwise band parallelization, ACE algorithm, support for ultrasoft & PAW...)
    
3.  This method requires commensurate k-point grids between QE and Wannier90. Certain k-point meshes may cause issues in Wannier90 when identifiying nearest neighbors, etc. It's recommended that you prepare a manual k-point grid with the utility located in wannier90/utility/kmesh.pl and use it in your QE calculation. Wannier90 does not recognize k-point symmetry, so it is a good idea to disable symmetry in your hybrid calculation with `nosym = .true` and `noinv = .true.` in the `&SYSTEM` block, along with the aforementioned manual k-points at the highest density you can afford, with corresponding q-point grid (as an aside, this type of grid is always needed for Wannier90, but normally you use this full grid with an nscf calculation after your automatic grid scf calculation when not using hybrid functionals, to reduce computational cost). I will leave it to you to determine what you need in terms of k- and q-point densities for your specific calculation.
    
4.  The input files you need at the beginning are: DFT input for QE, Wannier90 input file (.win), and a pw2wan input file. Here are some I used for a very quick (probably unconverged) calculation I did on my desktop, just using bulk silicon. In the interest of time I used automatic projections with the SCDM method and default values, you should read up on this and decide how you should proceed in your own calculation (manual projections require the `begin projections` block in Wannier90 input--read the user guide for more info). It can affect the band structure significantly.
    

QE input file: silicon.in

```
&control
    calculation = 'scf'
    restart_mode='from_scratch',
    prefix='Si-HSE',
    pseudo_dir = './',
    outdir='./TMP_DIR/'
 /
 &system    
    ibrav=  2, celldm(1) =10.20, nat=  2, ntyp= 1,
    ecutwfc =30.0,  nbnd = 8,
    input_dft='hse', nqx1 = 1, nqx2 = 1, nqx3 = 1, 
    x_gamma_extrapolation = .true.,
    exxdiv_treatment = 'gygi-baldereschi',
    nosym = .true., noinv = .true
 /
 &electrons
    mixing_beta = 0.7
 /
ATOMIC_SPECIES
 Si  28.086  Si_ONCV_PBE-1.1.upf
ATOMIC_POSITIONS alat
 Si 0.00 0.00 0.00 
 Si 0.25 0.25 0.25 
K_POINTS crystal
  0.00000000  0.00000000  0.00000000  1.250000e-01
  0.00000000  0.00000000  0.50000000  1.250000e-01
  0.00000000  0.50000000  0.00000000  1.250000e-01
  0.00000000  0.50000000  0.50000000  1.250000e-01
  0.50000000  0.00000000  0.00000000  1.250000e-01
  0.50000000  0.00000000  0.50000000  1.250000e-01
  0.50000000  0.50000000  0.00000000  1.250000e-01
  0.50000000  0.50000000  0.50000000  1.250000e-01
```

Wannier90 input file: silicon.win

```
! Silicon HSE 1
 num_wann    = 8
 num_bands   = 8
 num_iter    = 20
 kmesh_tol   = 0.0000001
 auto_projections = .true.

! Use as much precision as you can (at least 6 decimals) to prevent issues with matching to QE output
Begin Unit_Cell_Cart
-2.698804 0.0000 2.698804
 0.0000 2.698804 2.698804
-2.698804 2.698804 0.0000
End Unit_Cell_Cart

begin atoms_frac
Si 0.00  0.00  0.00
Si 0.25  0.25  0.25
end atoms_frac

!begin projections
!Si:sp3
!end projections

! To plot the WF interpolated bandstructure
bands_plot       = .true.
bands_num_points = 200

begin kpoint_path
L 0.50000  0.50000 0.5000 G 0.00000  0.00000 0.0000
G 0.00000  0.00000 0.0000 X 0.50000  0.00000 0.5000
X 0.50000 -0.50000 0.0000 K 0.37500 -0.37500 0.0000
K 0.37500 -0.37500 0.0000 G 0.00000  0.00000 0.0000
end kpoint_path

! KPOINTS

mp_grid : 2 2 2

begin kpoints
0.0 0.0 0.0
0.0 0.0 0.5
0.0 0.5 0.0
0.0 0.5 0.5
0.5 0.0 0.0
0.5 0.0 0.5
0.5 0.5 0.0
0.5 0.5 0.5
end kpoints
```

pw2wannier90 input file: silicon.pw2wan

```
&INPUTPP
 prefix = 'Si-HSE'
 outdir = './TMP_DIR'
 seedname = 'silicon'
 scdm_proj = .true.
 scdm_entanglement = 'isolated'
 scdm_mu = 0.0
 scdm_sigma = 1.0
/
```

Calculation Procedure
---------------------

1.  Run Wannier90 to generate some needed files, with the postprocessing option: `$ wannier90 -pp silicon`
2.  Run your QE hybrid functional calculation (obviously use the correct mpi commands for your system when running in parallel): `$ pw.x -inp silicon.in > silicon.out`
3.  Run pw2wannier: `$ pathtoqe/PP/src/pw2wannier.x -inp silicon.pw2wan`
4.  Run Wannier90 again to do the calculation and get band structure: `$ wannier90 silicon`

Doing the above I got this band structure. It obviously has some problems (some bands jumping up above the VBM) but the gap is larger than PBE and I did this with a very sparse grid, and no optimization of any options.

[![](https://i.stack.imgur.com/AlgQ1.jpg)](https://i.stack.imgur.com/AlgQ1.jpg)
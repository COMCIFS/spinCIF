A project for the development of a proposed CIF dictionary related to spin space groups.

__Background__

[Spin space groups](https://journals.aps.org/prx/abstract/10.1103/PhysRevX.14.031037) (sometimes referred to as 
"SSGs", but we will refrain from using that abbreviation here because of the prior use of "SSGs" to describe  [superspace groups](https://landau3.byu.edu/2011%20Stokes.pdf) in the context of incommensurately modulated crystal structures) are
joint symmetry groups of spatial and spin operations that leave a magnetic structure unchanged, particularly in materials where spin-orbit coupling (SOC) is negligible. By decoubling spin rotation and spatial rotation, spin space groups provide a more comprehensive classification of magnetic structures. Spin space groups have been found useful for identifying new types of topological electronic states and other aspects of magnetic crystal structure not characterizable by the magnetic space group (MSG) formalism.

__The Project__

This project aims to create a CIF standard for the description of spin space groups. This standard ("SpinCIF"; core_spin.dic) will import a subset of categories and objects from [core_mag.cif](https://github.com/COMCIFS/cif_mag) and add four spin spacegroup-specific categories, including (preliminary descriptions only): 

**SPACE_GROUP_SPIN**

The SPACE_GROUP_SPIN category describes the spin space group of the structure, including the orientation of the spin system with respect to the lattice that is used to describe the structure.

**SPACE_GROUP_SYMOP_SPIN_OPERATION**

The _SPACE_GROUP_SYMOP_SPIN_OPERATION category specifies the symmetry operations of the spin space group, excluding the trivial spin-only subgroup. It is mandatory, and (in conjunction with the operations described in the _SPACE_GROUP_SYMOP_SPIN_LATTICE category, if present) must include all operations of the non-trivial group. This is a similar category to space_group_symop_magn_operation used in magCIF for the loop, which specifies the symmetry operations of a magnetic space group. A difference here is that, in addition to the operation for the space coordinates, described with x,y,z symbols, and the “-1” or “+1”, to indicate the inclusion or not of time reversal, the spin point-group operation is also separately specified, as it is not determined by the space operation, as is the case for a  magnetic space group. A second difference here is that the spin part of the operation may use the mathematical function sqrt(x) and the division operation in order to avoid truncated irrational numbers within the description. For example, 1/sqrt(3)u-2/sqrt(3)v,2/sqrt(3)u-1/sqrt(3)v,w.


**SPACE_GROUP_SYMOP_SPIN_LATTICE**

The _SPACE_GROUP_SYMOP_SPIN_LATTICE category provides a loop for specifying the symmetry operations of  the so-called spin translation subgroup of the spin space group. It is a similar category to space_group_symop_magn_centering used in magCIF, and is formed by operations that  combine a space translation and a spin transformation. The same format is used as in the _SPACE_GROUP_SYMOP_SPIN_OPERATION category.  Similarly, The first entry, with id 1, must be the identity transform. As the operations forming the trivial spin-only subgroups are not listed in any case, specifying in this separate loop these spin translation operations allow  the operations listed in _SPACE_GROUP_SYMOP_SPIN_OPERATION to specify only a single representative for all operations having the same space point-group operation. The product of the operations listed in the two loops produces the full set of representative operations of the nontrivial spin space group. _SPACE_GROUP_SYMOP_SPIN_LATTICE is optional, as it is always possible to include all of the symmetry operations in _SPACE_GROUP_SYMOP_SPIN_OPERATION.. 


**ATOM_SITE_SPIN_MOMENT**

The _ATOM_SITE_SPIN_MOMENT category provides a loop for presenting magnetic moments of spin origin. This is a similar category to the CIF_core_mag.dic category _ATOM_SITE_MOMENT, which is used  to specify the magnetic moments without resolving the contributions of spin and orbital origin. Here the difference is that the magnetic moments given are supposed not to have any contribution of orbital orbital origin, as the transformation properties of moments of orbital origin for the spin space group operations are different. 


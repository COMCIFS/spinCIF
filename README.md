A project for the development of a proposed CIF dictionary related to spin space groups.

__Background__

[Spin space groups](https://journals.aps.org/prx/abstract/10.1103/PhysRevX.14.031037) (sometimes referred to as 
"SSGs", but we will refrain from using that abbreviation here because of the prior use of "SSGs" to describe  [superspace groups](https://landau3.byu.edu/2011%20Stokes.pdf) in the context of incommensurately modulated crystal structures) are
joint symmetry groups of spatial and spin operations that leave a magnetic structure unchanged, particularly in materials where spin-orbit coupling (SOC) is negligible. By decoubling spin rotation and spatial rotation, spin space groups provide a more comprehensive classification of magnetic structures. Spin space groups have been found useful for identifying new types of topological electronic states and other aspects of magnetic crystal structure not characterizable by the magnetic space group (MSG) formalism.

This project aims to create a CIF standard for the description of spin space groups. This standard ("SpinCIF"; core_spin.dic) will import a subset of categories and objects from [core_mag.cif](https://github.com/COMCIFS/cif_mag) and add four spin spacegroup-specific categories, including (preliminary descriptions only): 

**SPACE_GROUP_SPIN**


**SPACE_GROUP_SYMOP_SPIN_LATTICE**

**SPACE_GROUP_SYMOP_SPIN_OPERATION**

**ATOM_SITE_SPIN_MOMENT**

This category provides a loop for presenting magnetic moments of spin origin
This is a similar category to atom_site_moment used in magCIF for the loop that specifies the magnetic moments without resolving the contributions of spin and orbital origin. Here the difference is that the magnetic moments given are supposed not to have any contribution of orbital orbital origin, as the transformation properties of moments of orbital origin for the SpSG operations are different. The atomic magnetic moments of orbital origin, if known, must be specified in a different loop of a different category, say atom_site_orbital_moment. Although experimentally it is quite difficult to resolve spin and orbital contributions to the total moments, an orbital contribution may be allowed by non-coplanar SpSGs, and therefore this additional category, which will be seldom used is also included. These two categories can also be used for descriptions using a MSG if the spin and orbital contribution to the moments is resolved.
(The name of this category is provisional. The people from COMCIF should be consulted and probably it would be better in the end to have something shorter, to make it a direct child category of atom_site, as it is atom_site_ moment. For instance it could be atom_site_spinmoment and for the moments of orbital origin a similar category atom_site_orbitalmoment . It would be in this case convenient to introduce as alias these  alternatives for the name of these two categories)



The plan is to introduce four new CIF categories 


$$
\def\v#1{\overrightarrow#1}
\def\E{\v E}
\def\D{\v D}
\def\B{\v B}
\def\H{\v H}
\def\P{\v P}
\def\F{\v F}
\def\p{\partial}
\def\d{\:\mathrm d}
\def\ep{\epsilon}
\def\x{\wedge}
\def\dt{\p t}
\def\dS{\p S}
\def\norm#1{|\:#1\:|}
\def\dx{\d x}
\def\dL{\d\v L}
\def\dl{\d\v l}
\def\coul{4\pi\ep_0}
\def\oiint{\unicode{x222F}}
\def\ds{\d \v S}
\def\para{||}
$$

# PHYS144

> [GNU General Public License v3.0](https://github.com/zifeo/EPFL/blob/master/LICENSE) licensed. Source available on [github.com/zifeo/EPFL](https://github.com/zifeo/EPFL).

Fall 2014: General physics II

[TOC]

## 1. Charge and current

- **static electricity**
  - 2 opposite charges attract
  - charge conservation
- electrostatic induction : charges reorganized
- **current** : change of charge $I=\frac{\p Q}\dt$
  - Rowland experiment
  - charge is discrete
  - Wimshurt generator
  - Kelvin's thunderstorm
- **point charge** : located on a point without spatial extension
- **charge density**
  - volume $\rho(x,y,z)=\rho(r,\theta)$ : $Q=\iiint_t \rho\dt$
  - surface $\sigma(x,y)=\sigma(\theta,\phi)$ : $Q=\iint_S \sigma\dS$
  - line $\lambda(x)$ : $Q=\int_L \lambda\d L$
- **current density** : current per unit area **normal** to the flow, $\d I =J\dS_\perp$ or $\v j=\frac{I}{A}=\sigma E$
  - volume $J$ : $I=\int_S \v J·\d \vec S$
  - surface $J_s$ : $I=\int_b J_s\d b$

## 2. Coulomb's law
- Newton's thid law : $\v F_{12}=-\v F_{21}$
- Coulomb/Cavendish experiement
- **Coulomb's law** : $\v F =\frac{1}{4\pi\ep_0}\frac{Q_1Q_2}{r^2_{12}}\hat r_{12}$
  - electric constant (permittivity of free space) : $\ep_0 \approx 8.8·10^{-12}\quad Fm^{-1}$
  - $\frac{1}{4\pi\ep_0}\approx 9·10^9 \quad Nm^2C^{-2}$
  - $\hat r_{12}=\frac{\v r_{12}}{\norm {r_{12}}}$
- **superposition principle** : $\F=\sum_n F_n$
- mutual potential energy of charges : $U=W=\int F\dx=\frac{-Q_1Q_2}{4\pi\ep_0r}$

## 3. Electrostatic
- **electric field** : $\E=\frac{\F}{Q_t}=\lim_{Q_t\to 0}\frac{\F(Q_t)}{Q_t}\quad NC^{-1},Vm^{-1}$
  - infinite thin plane : $\E=\frac{\sigma}{2\ep_0}$
  - rod : $\E=\frac{\lambda}{2\pi\ep_0 x}$
  - in case of $r< r_0$ : take ratio $r/r_0$ as $r$
- **electric potential** : $V_{AB}=\frac{W_{AB}}{Q_t}=\int -\E·\dL\quad JC^{-1},V$
  - single charge as $V_\infty=0$: $V=\frac{Q}{\coul}\frac{1}{r}$
  - continuous distribution : $V=\frac{1}{\coul}\int\frac{\d q}{r}$
  - charged disk : $V=\frac{\sigma}{2\pi\ep_0}(\sqrt{a^2+b^2}-a)$
- electrical engery : $E=qV$
- **charges in E-fields** : $\F=Q\E=m\v a$
  - can accelerate particules $\v v_i || \E$
- Millikan experiment
- electronvolt : $1eV=1.6·10^{-19}J$ energy of $e^-$ passing $1V$ potential difference
- Ion propulsion
- **change of direction** : $\frac{\sin \alpha_1}{\sin \alpha_2}=\frac{v_2}{v_1}$
- **electric dipole** : $+q$ and $-q$ at distance $a$
  - **dipole moment** : $\v p = q\v a$
  - **potential** : $V_p=\frac{p\cos\theta}{4\pi\ep_0r^2}=\frac{\v p·\hat r}{4\pi\ep_0r^2}$
    - $E_\theta=-\frac{1}{r}\frac{\p V}{\p\theta}=\frac{p\sin\theta}{\coul r^3}$
    - $E_r=-\frac{\p V}{\p r}=\frac{2p\cos\theta}{\coul r^3}$
  - **in E-field** : dipole will align to E-field
    - torque : $\v\tau =\v p\x\E$
    - uniform E-field : $\sum\F=0$
    - potenial energy : $U=-pE\cos\theta=-\v p·\E$ ($U=0$ for $\theta=\pi/2$)
- multipoles
  - monopole : $V\propto\frac{Q}{r}$ and $E\propto\frac{Q}{r^2}$
  - dipole $\v p$ : $V\propto\frac{p}{r^2}$ and $E\propto\frac{p}{r^3}$ as $\sum Q=0$
  - quadrupole $\v q$ : $V\propto\frac{q}{r^3}$ and $E\propto\frac{q}{r^4}$ as $\sum Q=0$, $\sum\v p=0$
  - octupole : $V\propto\frac{1}{r^4}$ and $E\propto\frac{1}{r^5}$ as $\sum Q=0$, $\sum\v p=0$, $\sum\v q=0$

## 4. Electrodynamics
- **flux** : $\Phi=\int_A\E·\d\v A=\int_A\E_\perp\d\v A$ (positive when outwards normal to the area)
- **Gauss's law** : flux of E-field over any closed surface is equal to enclosed charge $\oiint\E·\d\v S=\frac{Q}{\ep_0}$
  - no E-field inside conductor, then all charge is located on surface of conductor (i.e. hollow conductor) $\oiint\E·\d\v S=0$
  - charge inside hollow conductor is screened
  - conducting sphere or shell (charge on surface)
    - inside $r\le r_0$ : $E=0$ so $\frac{\p V}{\p r}=0$ and $V=\frac{Q}{\coul r_0}$
    - outside $r\ge r_0$ : $E=\frac{Q}{\coul r^2}$ and $V=\frac{Q}{\coul r}$
  - thin plane conductor with surface charge : $\E=\frac{\sigma}{2\ep_0}$
- Gauss's divergence theorem : $\nabla·\E=\frac{\rho}{\ep_0}$ as $\iiint_V \text{div }\F·\d V=\oiint_{\d V}\F·\d\vec S$
- solid angle (3D angle) : $\Omega=\frac{\v S}{r^2}$ as $\d\Omega=\frac{\dS\cos\theta}{r^2}$
- Rutherford's experiment
- **point effect** : Corona discharge due to high field at sharp point (locally $E=\frac{V}{r_0}$)
  - for the same potential : $\sigma_{big}<\sigma_{small}$ and $E_{big}< E_{small}$
- **circuital law (only in electrostatic fields)** : $\oint\E·\d\v L=0$ or $\nabla\x\E=0$
- **Poisson's and Laplace's equation** : $\Delta·V=-\frac{\rho}{\ep_0}$ (if no charge $\Delta·V=0$)
  - solution only if boundary conditions are specified

## 5. Capacitance and dielectrics
- **capacitance** : amout of charge a conductor can hold for a given potential $C=\frac{Q}{V}\quad CV^{-1},F$
  - in vacuum : depend only on geometry
  - conducting sphere : $C=\frac{Q}{V}=\coul r_0$
  - ideal capacitor : $C=\frac{Q}{V_A-V_B}$ where $A$ and $B$ are the same charge (but opposite)
  - spherical capacitor : $C=\coul\frac{R_aR_b}{R_a-R_b}$
  - parallel plate capacitor : $C=\ep_0\frac{S}{d}$
  - cylindrical capacitor : $C=\frac{2\pi\ep_0 l}{\ln \frac{R_a}{R_b}}$
  - wires and transmission lines
    - co-axial : $C=\frac{2\pi\ep_0}{\ln\frac{b}{a}}$
    - twin wire : $C=\frac{\pi\ep_0}{\ln\frac{d}{r_a}}$
  - combinations of capacitors
    - series : $\frac{1}{C}=\sum_i\frac{1}{C_i}$
    - parallel : $C=\sum_iC_i$
- **polarization of matter** : shift of electron distribution, resulting in an induced dipole collection
- **dielectrics** : no true insulator exist, matter can be polarized
  - dipole moment per volume : $\v p=\v P\d\tau$
  - dipole moment at surface : $\sigma_p=\v P_\perp$
  - amout of charge that has moved through a surface : $Q_{polarized}=-\oiint\v P·\d\v S$
  - *off-topic* : $\vec J_p=\frac{\p\v P}{\dt}$ and $\E=\rho\v J$
- **electric susceptibility** : how easy it is to polarize a material $\v P=\ep_0\chi_e\E$
- **D-field** : displacement field $\D=\ep_0\E+\P$
  - $\oiint\D·\d\v S=\sum Q_{free}$ or $\nabla·\D=\rho_{free}$ (only conduction charges are source of D-field)
  - D-field is what you set, E-field is what you get
- **relative permittivity** : $\ep_r=1+\chi_e$ (E-field is reduced by factor $\E=\frac{\E_{ext}}{\ep_r}$)
- **electric energy** : $E=U_E=W=\frac{1}{2}\frac{Q^2}{C}=\frac{1}{2}CV^2=\frac{1}{2}QV=\frac{1}{2}\ep_0\int_\tau \ep_rE^2\d\tau=\frac{1}{2}\int_\tau\D·\E\d\tau$
- **capacitor with dielectric**
  - isolated ($Q$ constant) : $V_0=\frac{Q_0}{C_0}$, $\frac{C}{C_0}=\ep_r$
  - connected ($V$ constant) : $Q=V_0C=Q_0\ep_r$
- **E- and D-field across interfaces(in a capacitor)**
  - outside dielectric : $\E=\E_{ext}=\frac{\sigma_c}{\ep_0}$ and $\D=\ep_0\E=\sigma_c$
  - inside dielectric : $\E=\frac{\E_{ext}}{\ep_r}=\frac{\sigma_c}{\ep_0\ep_r}$ and $\D=\ep_0\ep_r\E=\sigma_c$
- **forces between charged conductors**
  - constant $Q$ : $\F=-\nabla U_E$
  - constant $V$ : $\F=+\nabla U_E$
- **piezoelectricity** : charge accumulated when stressed
- **pyroelectricity** : voltage when heated/cooled
- **ferroelectricity** : spontaneous polarization

## 6. Circuits
- AC/DC networks : alternative current vs direct current
- **resistivity** $\rho$ : $\rho=\frac{1}{\sigma}=\frac{RA}{l}\quad \Omega m$
- **conductivity** $\sigma$ : $\v j=\sigma\E$
- **Ohm's law** : $V=RI$
- **resistance** : $R=\frac{\rho l}{A}$ (dependence on material and on temperature)
- Drude model
- **Kirchhoff's laws** : $\sum_i I_i=0$ and $\sum_i \Delta V_i=0$
- **energy dissipation** (heat) : $P=IV=RI^2=\frac{V^2}{R}$
- combination of capacitor and resistor
- **delta-star transformation**
- **capacitor** : $V_C(t)=V_0(1-e^{-t/\tau})$ and $I(t)=C\frac{\d V_C}{\dt}$
- **measurement schemes**
  - voltage : across contacts (high internal resistance)
  - current : between contacts (low internal resistance)
- **wheatstone bridge** : $R_xR_1=R_2R_3$

## 7. Electromagnetism
- comparison to electrostatics : **no monopole**, not a central force, only based on B-field
- **current element** : $I\d\v l$
- Oersted experiment
- Ampère's experiment
- **forces on currents** : $\F=\oint_LI\d\v l\x\B$
- **torque** : $\v\tau=I\v A\x\B$
- **Biot-Savart law** (magnetic field due to current) : $\d\B=\frac{\mu_0 I\ds\x\hat r}{4\pi r^2}$
  - $\B=\oint_L\frac{\mu_0I\dl\x\hat r}{4\pi r^2}=\iiint_V\frac{\mu_0\v j\x\hat r\d\tau}{4\pi r^2}$
  - rectangular conducteur : $\B=\frac{\mu_0I}{2r}$
  - thick wire : $\B=\frac{\mu_0 I}{2\pi r}$
  - center of coil : $\B=\frac{\mu_0 I}{2 r}$
- **permeability **of free space : $\frac{\mu_0}{4\pi}=10^{-7}$
- Helmholtz coils : constant B-field between two coils $\frac{\d^2 B_x}{\d x^2}=0$
- **Solenoid** : $B_x=\mu_0nI$ where $n$ is the number of windings per unit length
- **force between currents** : $F=\frac{\mu_0I_1I_2l}{2\pi r}$ (attract if same direction)
- **Lorentz force** : $\F=q\v v\x\B$
- **B-field due to moving charge** : $\B=\frac{\mu_0q\v v\x\hat r}{4\pi r^2}$
  - parallel : $\F=0$
  - perpendicular : $\F\perp\v v$
- **circular motion** : $a=\frac{v^2}{r}$ resulting $r=\frac{mv}{qB}$
- Bubble chamber, magnetic deflector, mass spectrometer
- **charged particule in homogenous B-field** : particle will travel on spiral path
- **charged particule in non-homogenous B-field** : magnetic mirror, Van Allen belt
- **combination of B- and E-fields** : E-field determines kinectic energy, B-field determines momentum, together determines velocity
  - special case $F=0$ : $V=\frac{E}{B}$
- **Hall effect** : current through conductor in B-field, measure voltage perpendicular to current $\F=e\v v_d\x\B$ with speed $v_d=\frac{BI}{net}=\frac{R_H BI}{t}$ where $R_H=\frac{1}{ne}$
- **magnetic dipole** : $\v m =I\v A$
  - $\F =0$ (non-uniform field $\F=(\v m·\nabla)\B$)
  - **torque** : $\v T=I\v A\x\B$
  - potential energy : $U=-\v m·\B$
  - angular momentum : $\v L =m_er^2\omega$ ($\omega=\frac{2\pi}{T}$)
  - **circular current** : $I=\frac{e\omega}{2\pi}$
  - gyromagnetic ratio : $\v m=\gamma\v L$ where $\gamma=\frac{e}{2m_e}$ (electron around atom)
  - Landé g-factor : $g=\frac{2m_e}{e}\gamma$ for free electron $g\approx 2$
  - Larmor procession : $\v T\perp\v L$ and $\d\v L =\v T\dt$
    - frequency : $\nu_L=\frac{\omega_L}{2\pi}=\frac{-\gamma}{2\pi}B$ with $\omega=\frac{T}{L\sin\theta}$
- **magnetic field** : $B_r=\frac{2\mu_0 m\cos\theta}{4\pi r^3}$ and $B_\theta=\frac{\mu_0m\sin\theta}{4\pi r^3}$
- **magnetic flux** : $\Phi=\int_A\B·\d\v A$
  - flux cut in time : $\d\phi=B\d A=Bvl\dt$ (Solenoid $\Phi=B·nA$)
  - potential energy : $U=-I\Phi$
  - find force : $F_x=-\frac{\p U}{\p x}=I\frac{\p \Phi}{\p x}$
  - find torque : $T_\theta=-\frac{\p U}{\p \theta}=I\frac{\p \Phi}{\p \theta}$
- **Ampère's circuital law** : $\oint_L\B·\d\v L=\mu_0I$
  - B-field due to coil : $\B=\mu_0 n I$
- **Gauss's law for B-fields** : $\oiint_S \B·\d\v S=0$
- **magnetic vector potential** : $\B=\nabla\x\v A$

## 8. Electromagnetic induction
- Faraday's experiments : a voltage or electromotance $V_{emf}=U_{indu}=-\frac{\d\Phi_m}{\dt}$ is induced when
  - a rigid stationary circuit across which there is a varying magnetic field
  - a rigid circuit moving in a B-field such that the magnetic flux through it changes
  - a part of a circuit which moves and cuts magnetics flux
- **motional electromotance** : moving conductor in B-field $\Delta V_{emf}=El=Bvl=\E·\d\v l=\frac{\d\Phi}{\dt}$
- **Lenz's law** : the direction of any magnetic induction effect is such as to oppose the cause of the effect
- **AC-generator** (rotating coil in B-field) : $N$ turns give $\Delta V_{emf}=-\frac{\d\Phi}{\dt}=NAB\omega\sin\omega t$
- **induced electric field** : $V_{emf}=\oint_L\E·\d\v L\not=0$ and $\nabla\x\E=-\frac{\p\B}{\p t}$ (electric field is no longer conservative in presence of changing magnetic field)
- **self-inductance** : $L=\frac{\Phi_{tot}}{I}=\mu_0 n^2 l A$ where $\Phi=LI$ and $\Delta V=-L\frac{\d I}{\dt}$
- **mutual inductance** : $\Phi_2=M_{12}I_1$ and $\Phi_1=M_{21}I_2$ with $M$ determined by geometry (in general same $M$) thus $\Delta V_{emf2}=-M\frac{\d I_1}\dt$
  - outer/inner solenoid : $M=\mu_0 n_1 n_2 A$
- **coupled circuits in general** : coefficient of coupling $k=\frac{M}{\sqrt{L_1L_2}}$
  - ideal transformer : $\frac{V_2}{V_1}=-\frac{n_2}{n_1}=-\frac{1}{N}$ and $N=\frac{I_2}{I_1}$
- **Tesla coil**

## 9. Magnetic materials
- **B-field in null in absence of external field** (except for ferromagnetic)
- **relative permeability** : $\mu_r=\frac{L_m}{L_0}=\frac{\Phi_m}{\Phi_0}=\frac{B_m}{B_0}$ and $\B=\mu_r\B_0$
- **magnetisation** : $\B=\B_0+\B_M$ and $\d\v m=\v M\d\tau$
- **H-field** : the H-field is what you set, the B-field what comes out $\H=\frac{\B}{\mu_0}-\v M$ (only free currents are sources of H-field)
  - circuital law : $\oint_L\H·\d\v l=I$ and $\nabla·\H=\v j$
  - magnetic susceptibility : $\v M=\chi_m\H$, $\mu_r=1+\chi_m$ and $\B=\mu_0\mu_r\H$
  - hollow solenoid $\H=nI$, $\chi_m=0$ (nothing), $\v M =0$ :$\B=\mu_0 n I$
    - if non empty : $\B=\mu_0(1+\chi_m)n I$
- **magnetic screening** : $\mu_{r2}B_{\para 1}=\mu_{r1}B_{\para 2}\quad B_{\perp 1}=B_{\perp 2}$
- **magnetic response of types of materials** $F_x\approx\frac{1}{2}\mu_0\chi_m\frac{\p H^2}{\p x}$
  - diamagnetisc : no resultant magnetic moment in materials (graphite, water, gold, etc.)
  - paramagnetic : resultant atomic magnetic moment but not ordered
  - ferromagnetic : metallic, large positive $\chi_m$, strong dependence on $H$ and history, become parmagnetic above critical temperature
    - resultant atomic magnetic moments : parallel order resulting in spontaneous magnetisation
  - antiferromagnetic : small positive $\chi_m$, dependence on $H$ and history with critical temperature
  - ferrimagnetic : like ferromagnetic, but non-metallic
  - at Curie's temperature : ferro/ferri become para
- **spin** : intrinsic magnetic moment of elements (and other elementary particles)
- Stern-Gerlach experiment
  - if electron paired : no resultant magnetic moment
  - if there are unpaired electrons not all spin in cancelled : resultant magnetic moment
- **hysteresis cycle in ferromagnets** : $E=W=\oint B\d H=\oint H\d B$

## 10. Electromagnetic waves
- **Maxwell's model is for slowly varying field in vacuo**
  - for rapidly varying field : $\nabla\x\B=\mu_0\v J+\mu_0\ep_0\frac{\p\E}{\p t}$ or $\oint_L\B·\d\v L=\mu_0I_c+\mu_0\ep_0\frac{\d}{\dt}\iint_S\E·\d\v S$
- paradox in Ampère's circuital law for B-field (only for charging the capacitor) : added displacement current : $\oint_L\B·\d\v L=\mu_0(I_c+I_d)$
- **electromagnetic waves in vacuo** (without sources $Q=0$ and $I=0$)
  - energy flux : $\v S=\frac{1}{\mu_0}\E\x\B$
  - energy density : $E=\frac{\ep_0\E^2}{2}+\frac{\B^2}{2\mu_0}$
  - quantity of movement : $\v p=\ep_0\E\x\B=\frac{1}{c^2}\v S$
- **wave equations** : $c^2=\frac{1}{\ep_0\mu_0}$
- **electromagnetic spectrum** : $E_{emw}=h\nu=\frac{hc}{\lambda}$ where Planck's constant $h=6.626·10^{-34}\quad Js$ with $\nu=f\lambda$ and $E=cB$
- **monochromatic plane wave** : Gauss $E(x,z,t)$, $B(x,y,t)$, faraday $\frac{\p E}{\p x}=-\frac{\p B}{\p t}$ and ampère $\frac{\p B}{\p x}=-\ep_0\mu_0\frac{\p E}{\p t}$
  - polarzitation : oscillation direction of E-field
  - relative magnitude : $\E=c\B$ and $\E\perp\B$ in phase
- **EM waves in a non-conducting medium** : velocity $c_m=\frac{c}{\sqrt{\ep_r\mu_r}}$ (non-ferromagnetic : $c_m=\frac{c}{\sqrt{\ep_r}})$) with refractive index $n=\frac{c}{c_m}\approx\sqrt{\ep_r}$
- Cherenkov radiation : $\ep_r>1$ means $c_m< c$ but particles can have speed larger as $c_m$
- **EM at boundaries of dielectrics** : $\nu_1=\nu_2$, $n_1\sin\theta_1=n_2\sin\theta_2$
  - critical angle (in the split of materials) : $\sin\theta_c=\frac{n_2}{n_1}$
  - total internal reflection : same angle
- **generation of electromagnetic waves** : $\frac{\p\E}{\p t}\not=0$, $\frac{\p\B}{\p t}\not=0$ only if $\frac{\p\v I}{\p t}\not=0$
  - if $Q=0$, $I=0$ : only propagation, no generation
  - if $Q$ constant, $I=0$ : E-field is steady
  - if $Q$ moves at constant speed, $I$ constant : B-field is steady
- synchrotron radiation : changing direction is also an acceleration
- **dipole radiation and antenna** : general rule of thumb $length=\lambda/2$
- **Maxwell's equations**
  - Gauss's law : $\nabla·\E=\frac{\rho}{\ep_0}$ or $\oiint_S\E·\d\v S=\frac{q}{\ep_0}$
  - Gauss's law for B-field : $\nabla·\B=0$ or $\oiint_S\B·\d\v S=0$
  - Circuital law : $\nabla\x\E=-\frac{\p\B}{\p t}$ or $\int_L\E·\d\v L=-\frac{\d}{\dt}\iint_S\B·\d\v S$
  - Ampère's circuital law : $\nabla\x\B=\mu_0\v I+\frac{1}{c^2}\frac{\p\E}{\p t}$ or $\oint_L\B·\d\v L=\mu_0 I$

## Comparison

|                              | Electricité                              | Magnétisme                               |
| ---------------------------- | ---------------------------------------- | ---------------------------------------- |
| density                      | charge $\rho(\v x,t)$                    | current $\v j(\v x, t)$ with $I=\iint_S \v j(\v x)·\ds$ |
| monopôle                     | $q=\iiint \rho(\v x)\d\v x$              | none (due to $\nabla·\B=0$)              |
| force                        | Coulomb $\v F =\frac{1}{4\pi\ep_0}\frac{Q_1Q_2}{r^2_{12}}\hat r_{12}$ | Lorrentz $\F=q\v v\x\B$, currents $\F=\oint_L I\dl\x\B$ |
| field                        | $\E=\frac{\F}{Q_2}=\frac{1}{4\pi\ep_0}\frac{Q_1}{r^2}\hat r$ | $\B=\frac{\mu_0I}{2\pi r}\hat e_\theta$  |
| if variates, creates         | $\B$                                     | $\E$                                     |
| potential                    | $V=-\int\E·\dl$                          | $\nabla\x\mathbb A=\B$                   |
| energy                       | $E=Vq$                                   | $E=-\v m·\B$                             |
| medium ($c^{-2}=\ep_0\mu_0$) | permittivity $\ep=\ep_0\ep_r$ (vaccum: $\ep_0=\frac{10^7}{4\pi c^2}$) | permeability $\mu=\mu_0\mu_r$ (vacuum: $\mu_0=4\pi10^{-7}$) |
| Gauss's law                  | $\oiint\E·\d\v S=\frac{Q}{\ep_0}$        | $\oiint_S \B·\d\v S=0$                   |
| Ampère's circuital law       | $\oint\E·\d\v L=0$ (if no variation)     | $\oint_L\B·\d\v L=\mu_0I$                |
| dipôle                       | $+q$ & $-q$ at distance $a$              | current $I$ loop of area $A$             |
| moment                       | $\v p = q\v a$                           | $\v m =I\v A$                            |
| torque                       | $\v T =\v p\x\E$ (align on $\E$)         | $\v T=I\v A\x\B$(align on $\B$)          |
| medium interface             | $E_{\para 1}=E_{\para 2}\quad\ep_{r1}E_{\perp 1}=\ep_{r2}E_{\para 2}$ | $\mu_{r2}B_{\para 1}=\mu_{r1}B_{\para 2}\quad B_{\perp 1}=B_{\perp 2}$ |
| modifier                     | polarization $\P=\ep_0\chi_e\E=\frac{\p\v p}{\p V}$ | magnetisation $\v M=\chi_m\H=\frac{\p \v m}{\p V}$ |
| susceptibility               | $\chi_e$ with $\ep_r=1+\chi_e$           | $\chi_m$ with $\mu=1+\chi_m$             |
| process                      | induction $\D=\ep_0\E+\P=\ep_0\ep_r\E$   | excitation $\H=\frac{1}{\mu_0}\B-\v M=\frac{1}{\mu_0\mu_r}\B$ |
| di/dia                       | insulator (can be slighlty polarized)    | $\chi_m\sim 10^{-5} < 0$: creates opposing B-field |
| piezo                        | polarized under pressure                 | magnetized under pressure                |
| para                         | polarization under E-field               | $\chi_m\sim 10^{-3}>0$: moment inordered, magnetized under B-field |
| ferro/ferri                  | spontaneous electric polarization        | $\chi_m\sim 10^5>0$: moment parallel ordered, hysteresis after E-field |

## Appendix
- $2\sin^2 t = 1-\cos 2t$
- $2\cos^2 x = 1+\cos 2x$
- $\sin 2x = 2\sin x \cos x$
- $\sin(a+b)=\sin a\cos b+\cos a\sin b$
- $\cos(a+b)=\cos a\cos b-\sin a\sin b$
- $\tan^2 x +1=\frac{1}{\cos^2 x}$
- $\cot^2 x +1=\frac{1}{\sin^2 x}$
- $\sin 0 = \frac{1}{2}\sqrt{0} = \cos \pi/2 = 0$
- $\sin \pi/6 = \frac{1}{2}\sqrt{1} = \cos \pi/3 = \frac{1}{2}$
  - $\sin \pi/4 =\frac{1}{2}\sqrt{2} = \cos \pi/4 =\frac{\sqrt{2}}{2}$
- $\sin \pi/3 = \frac{1}{2}\sqrt{3} = \cos \pi/6=\frac{\sqrt{3}}{2}$
- $\sin \pi/2 = \frac{1}{2}\sqrt{4} = \cos 0 = 1$
- $\cosh z =\frac{e^z+e^{-z}}{2}$
- $\sinh z =\frac{e^z-e^{-z}}{2}$
- $\cos z =\frac{e^{iz}+e^{-iz}}{2}=\cosh iz$
- $\sin z =\frac{e^{iz}-e^{-iz}}{2i}=\frac{\sinh iz}{i}$
- $e^z=\cosh z +\sinh z=\cos z+i\sin z$
- $e^{-z}=\cosh z -\sinh z$
- $\cosh^2 z -\sinh^2 z = 1$
- $\sin mx\cos nx=\frac{1}{2}[\sin (m+n)x + \sin (m-n)x]$
- $\cos mx\cos nx=\frac{1}{2}[\cos (m+n)x + \cos (m-n)x]$
- $\sin mx\sin nx=\frac{1}{2}[\sin (m-n)x - \cos (m-n)x]$

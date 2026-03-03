# Lecture: The Origin of Magnetism - From Electronic Structure to Exchange Interactions

## Lecture Overview

1.  **Introduction:** Macroscopic magnetism and its microscopic mystery.
2.  **Part I: The Atomic Origin - Electrons as Tiny Magnets.** How orbital and spin angular momentum create atomic magnetic moments .
3.  **Part II: From Atoms to Solids - The Role of Electronic Structure.** Why simply having unpaired electrons isn't enough for permanent magnetism .
4.  **Part III: The Stoner Criterion - A Condition for Magnetism in Metals.** A quantitative model for when a metal becomes ferromagnetic .
5.  **Part IV: The Exchange Interaction - The Glue of Magnetic Order.** The quantum-mechanical "force" that aligns spins .
6.  **Conclusion:** Tying it all together.

---

## Introduction

We're all familiar with magnets – they're on our refrigerators, in our speakers, and inside every hard drive. But if you take a bar magnet and cut it in half, you don't get one north pole and one south pole. You get two smaller, complete magnets. Cut those in half again, and you get even more magnets. This hints that the source of magnetism is not some macroscopic property, but is fundamental to the very atoms that make up the material.

Here, we're going to dive deep into the atomic and electronic world to answer a seemingly simple question: **why are some materials magnetic?**

## Electrons as Tiny Magnets

The story begins not with the atom as a whole, but with its electrons. For a long time, we understood that electric currents could create magnetic fields, as described by Ampère. But what creates a magnetic field in a permanent magnet, where there's no obvious battery or current?

The answer lies in the inherent properties of the electron itself. When a magnetic moment $\mathbf{m}$ is placed in an external magnetic field $\mathbf{B}$, it experiences a torque that tends to align it with the field:

$$\pmb{\tau} = \mathbf{m} \times \mathbf{B}$$

This torque is fundamental to understanding how magnetic moments respond to applied fields. The collective behavior of many such moments leads to the macroscopic property of **magnetization** $\mathbf{M}(\mathbf{r})$, defined as the volumetric density of magnetic moments:

$$\mathbf{M}(\mathbf{r}) = \frac{\mathrm{d}\mathbf{m}}{\mathrm{d}V}$$

There are two contributions to an electron's magnetic moment:

1.  **Orbital Angular Momentum:** You can think of an electron orbiting the nucleus as a tiny loop of electric current. This circulating charge creates a magnetic field, just like a microscopic electromagnet. The orbital magnetic moment is related to the orbital angular momentum $\mathbf L = \mathbf r_j \times (m_e \mathbf v_j)$ by:

    $$\mathbf{m}^{\mathrm{orb}} = -\frac{\mu_{\mathrm{B}}}{\hbar} \mathbf{L}$$

    where the minus sign reflects the negative charge of the electron.

2.  **Electron Spin:** This is a purely quantum-mechanical property with no classical analog. The electron behaves as if it is spinning on its own axis, and this intrinsic "spin" $\mathbf{S}$ gives it an additional magnetic moment:

    $$\mathbf{m}^{\mathrm{spin}} = \frac{\mu_{\mathrm{B}}}{\hbar} g_e \mathbf{S}$$

In both expressions, we encounter the **Bohr magneton** $\mu_{\mathrm{B}} = e\hbar/2m_e$, the fundamental quantum of magnetic moment for an electron. The quantity $g_e$ is the **Landé g-factor**, which for a free electron is approximately:

$$g_e = 2\left(1 + \frac{\alpha}{2\pi} + \mathcal{O}(\alpha^{2})\right) \approx 2.0023$$

where $\alpha = 1/137$ is the fine-structure constant. For most practical applications, we can take $g_e = 2$.

In an atom, these orbital and spin angular momenta combine to give the total magnetic moment:

$$\mathbf{m} = \frac{\mu_B}{\hbar} \sum_j(\mathbf{L}_j + 2\mathbf{S}_j)$$

In atoms with completely filled electron shells, the total angular momentum cancels out to zero. **For every electron spinning up, there's one spinning down, and for every orbital motion in one direction, there's one in the opposite direction.** These atoms have no permanent magnetic dipole moment and are called **diamagnetic**.

Magnetism requires **unpaired electrons**. In atoms with partially filled shells, like the transition metals iron, cobalt, and nickel, there are unpaired electrons. Their spin and orbital moments don't cancel, giving the atom a net magnetic moment.

## Isolated atom

The magnetic moment of an atom originates from the orbital and spin angular momenta of its electrons. In a hydrogen atom, each electron state is characterized by four quantum numbers:

- **Principal quantum number $n$**: Associated with the number of radial nodes in the wavefunction
- **Orbital angular momentum quantum number $l$** (azimuthal): Satisfies $\langle L^2 \rangle = \hbar^2 l(l+1)$, where $0 \leq l \leq n-1$
- **Magnetic quantum number $m_l$**: Eigenvalue of the $z$-component of orbital angular momentum, $\langle L^z \rangle = \hbar m_l$, with $-l \leq m_l \leq l$
- **Spin quantum number $m_s$**: Associated with the $z$-component of spin angular momentum, $\langle S^z \rangle = \hbar m_s$, where $m_s = \pm 1/2$

States with the same $n$ form a **shell**. Within each shell, states with the same $l$ form a **subshell** (labeled $s, p, d, f$ for $l = 0,1,2,3$). Each orbital (specific $m_l$) has two channels for the two possible $m_s$ values.

### Ground State Determination and Hund's Rules

For an isolated atom in its ground state, electrons fill orbitals according to:

1. **Pauli's exclusion principle**: No two electrons can share the same set of quantum numbers
2. **Energy ordering**: Orbitals with lowest energy (depending on $n$ and $l$) are filled first
3. **Hund's rules** (priority within each subshell):
   - **First rule**: Electrons occupy orbitals to maximize total spin $S$. Each orbital in a subshell gets one electron with parallel spins before doubling occupancy. This minimizes Coulomb repulsion.
   - **Second rule**: For a given $S$, maximize total orbital angular momentum $L$. Spin-spin and orbital-orbital interactions are both ferromagnetic, with spin-spin being stronger.
   - **Third rule**: Total angular momentum $J$ is given by $J = |L - S|$ if the subshell is less than half-full, or $J = L + S$ if more than half-full. For half-full subshells, $L = 0$ so $J = S$. These differences arise from spin-orbit coupling.

**Important consequence**: Full subshells have no net angular momentum—for every electron with $m_s$, there's one with $-m_s$, and similarly for $m_l$. This explains why noble gases are non-magnetic.

## In solids: localized Magnetism

Elements that retain their magnetic moments in solids typically have magnetic moments from inner incomplete subshells (like $3d$, $4f$ electrons). These electrons are:

- Less involved in chemical bonding
- Well-localized at their crystal sites
- Characteristic of magnetic insulators

However, observed magnetic moments in solids often differ from isolated atoms. Notably, orbital angular momentum $L$ is often quenched due to the nonspherical electrostatic potential from surrounding atoms in the crystal.


- **Full subshells have no net angular momentum**: For every electron with spin projection $m_s$, there is one with $-m_s$, and similarly for opposite azimuthal quantum numbers (noble gases are prime examples)
- **Most elements have net magnetic moments when isolated**: Since most atoms have incomplete subshells, they possess net angular momentum and therefore magnetic moments
- **Localized magnetism in solids**: Elements with magnetic moments from inner incomplete subshells can retain their magnetism in solids because these electrons are less involved in bonding
- **Characteristic features**: The magnetic electrons remain well-localized at their crystal sites, typical of **insulators**
- **Orbital angular momentum quenching**: The observed magnetic moment in solids often differs dramatically from the isolated atom case
- **Primary cause**: The orbital angular momentum $L$ is particularly affected—it is "quenched" due to the **nonspherical electrostatic potential** from surrounding atoms in the crystal lattice



## Part II: From Atoms to Solids - The Role of Electronic Structure

So, if an iron atom has unpaired electrons and a magnetic moment, why isn't a piece of iron always magnetic? The answer is that while each atom is a tiny magnet, in a solid, these atoms are packed closely together. Their interactions are governed by the **electronic structure** of the solid, specifically the formation of energy bands.

When atoms come together to form a solid, their discrete atomic energy levels broaden into continuous bands. For magnetism, the most important is the **d-band**, particularly in 3d transition metals. This band is narrow and has a very high **density of states (DOS)** at the Fermi level, `D(E_F)` .

A high density of states means there are many available energy levels for electrons near the Fermi energy. As we will see, this is a crucial prerequisite for magnetism. The question becomes: what makes it energetically favorable for these unpaired spins to all point in the same direction, creating a permanent, bulk magnet?

## Part III: The Stoner Criterion - A Condition for Magnetism in Metals

This is where the **Stoner model**, named after Edmund Clifton Stoner, comes in . It provides a simple and powerful criterion for when a metal will become ferromagnetic. It's known as the **Stoner criterion** .

Imagine the energy bands for spin-up and spin-down electrons. In a non-magnetic material, these bands are exactly aligned. There are an equal number of spin-up and spin-down electrons.

The Stoner model says that if we try to make the material magnetic by shifting the bands relative to each other (a process called **exchange splitting**), there is an energy cost. We have to promote some electrons from the spin-down band to higher energies in the spin-up band. The cost is related to the **kinetic energy**, which is inversely proportional to the density of states `D(E_F)`. A high `D(E_F)` means the energy cost for this redistribution is low.

However, there is also an energy gain. This comes from the **exchange interaction** (which we'll discuss in the next section), represented by the Stoner parameter `I` . This interaction lowers the energy of the system when spins are aligned.

Ferromagnetism occurs when the energy gain from aligning spins outweighs the kinetic energy cost. This competition leads to the famous **Stoner criterion**:

$$ I \cdot D(E_F) > 1 $$

Let's break this down :
- **`I` (Stoner Parameter):** A measure of the strength of the exchange interaction in the material. It is essentially the energy gain you get from making two electrons parallel.
- **`D(E_F)` (Density of States at the Fermi Level):** A measure of how many electronic states are available at the Fermi energy. A high value means it's "easy" for electrons to rearrange themselves into a spin-polarized state without a huge kinetic energy penalty .

If the product of these two terms is **greater than 1**, the non-magnetic state is unstable, and the material will spontaneously become ferromagnetic. It will lower its total energy by developing a net magnetic moment. This elegantly explains why only certain metals, like iron, cobalt, and nickel (which have a high `D(E_F)` in their 3d band), are ferromagnetic at room temperature, while others with lower `D(E_F)` are not .

## Part IV: The Exchange Interaction - The Glue of Magnetic Order

The Stoner criterion uses an exchange parameter `I`, but what is the physical origin of this interaction? It is not the familiar magnetic dipole-dipole interaction, which is far too weak to explain the high ordering temperatures (like the Curie temperature of 1043 K in iron) .

The true origin is the **exchange interaction**, a direct consequence of the **Pauli Exclusion Principle** and the **Coulomb repulsion** between electrons .

Here's how it works, as described in multiple sources :
- The Pauli Exclusion Principle states that two electrons cannot occupy the same quantum state. This means that two electrons with the **same spin** (parallel) cannot be in the same location in space.
- Two electrons with **opposite spins** (antiparallel) have no such restriction. They can, in principle, occupy the same spatial region.

Because same-spin electrons are forced to avoid each other, they are, on average, further apart. This reduces their electrostatic **Coulomb repulsion**, which is a very large energy . The energy of the system is therefore lower when electrons have parallel spins.

This effective interaction, which favors parallel spin alignment, is called the **exchange interaction**. It is often described by the Heisenberg Hamiltonian :

$$ H_{ex} = -2J \sum_{i \neq j} \mathbf{S}_i \cdot \mathbf{S}_j $$

In this equation, `J` is the **exchange integral**. A positive `J` means that parallel alignment (`S_i` and `S_j` in the same direction) lowers the energy, leading to ferromagnetism . This `J` is directly related to the Stoner parameter `I` in the band model. The strength of this interaction, and thus the Curie temperature, is determined by the overlap of electron orbitals from neighboring atoms .

## Conclusion

To conclude, the origin of magnetism is a multi-scale phenomenon:
1.  **At the atomic level**, it requires atoms with unpaired electrons, giving them a net magnetic moment .
2.  **In the solid state**, these atoms interact. The **Stoner criterion**, `I * D(E_F) > 1`, provides the condition for a metal to spontaneously become ferromagnetic, emphasizing the crucial role of a high density of states at the Fermi level .
3.  The fundamental "force" that locks these moments into a permanent, parallel alignment is the **exchange interaction** – a quantum-mechanical effect born from the Pauli Exclusion Principle and Coulomb repulsion, which makes it energetically favorable for electrons to keep their spins parallel .

This elegant interplay of quantum mechanics and electrostatics is what gives us the permanent magnets that are so essential to modern technology.

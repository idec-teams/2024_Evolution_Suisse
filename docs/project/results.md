# Results



## Development of an E3 ligase PACE evolutionary system
### Ubiquitination-dependent selection logic
To evolve the SIAH1/2 E3 ubiquitin ligases using the PACE system, we needed to link the ligase’s activity directly to phage propagation. To achieve this, we utilised a modified T7 bacteriophage RNA polymerase (RNAP) that had been split into two halves. Normally, this split RNAP is inactive unless both halves are brought close together within the cell, forming a complete, functional complex. We designed a system where the RNAP halves would only assemble if the E3 ligase successfully ubiquitinated its target.

In this setup, one half of the RNAP is fused to ubiquitin, while the other half is fused to a substrate that can be ubiquitinated. If SIAH1/2 (E3) ubiquitinates the substrate, the two RNAP halves are brought close enough to combine, forming a complete RNAP capable of transcribing genes. We took advantage of this by placing the gene _gIII_ (coding for pIII, a protein crucial for phage propagation) under the control of a T7 promoter, which only the assembled RNAP can activate. As a result, phages can only propagate if SIAH1/2 effectively ubiquitinates the target, tying the phage’s propagation to the ligase’s activity. Additionally, we also designed a system that could select against specific off-target effects (Figure X). To this end, we would add an additional genetic circuit which ‘punished’ E3 ligases that recognised unwanted targets. Instead of the substrate towards which we want to evolve, we fuse the unwanted protein (dubbed the mock substrate) to the C-terminal  RNAP subunit. This could be the original canonical substrate of the E3 or a protein recognized as an off-target in later stages of the SIAH1/2 evolution. If this mock substrate is recognized by a SIAH1/2 variant it would also trigger the formation of a functioning RNAP through the ubiquitination of the mock substrate. Crucially, the C-terminal RNAP fused to the mock substrate differs from the one present in the positive selection as it does not bind this T7 promoter sequence, but a slightly altered one. This ensures that one can perform the positive and negative selection at the same time. The altered T7 promoter sequence (*PT7; Figure X) is then recognized by the negative selection RNAP which leads to the transcription of a mock _gIII_. Phages that incorporate the encoded protein are essentially unable to infect new cells, leading to the washout of phages carrying SIAH1/2 variants that recognize unwanted substrates.

<figure markdown>
![Figure_positive_negative_selection](https://idec-teams.github.io/2024_Evolution_Suisse/img/result figures/E3_selection_V1.png)
<figcaption> Figure X: Selection logic for SIAH1/2-dependent _gIII_ expression. (a) Split T7 RNAP subunits fused to ubiquitin or a canonical substrate of SIAH1/2. The presence of E1, E2 and E3 (SIAH1/2) should lead to the assembly of the T7 RNAP subunits and thereby gIII transcription under the control of a T7 promoter. (b) Potential off-target effects of the evolved SIAH1/2 could be selected against by punishing spurious ubiquitination of a mock substrate by E3 ligase. In a new AP1neg plasmid, a mutated version of the C-term RNAP subunit that recognises a modified T7 promoter sequence [1] is fused to a mock substrate. A non-functional gIII (here, mock _gIII_) is placed under the control of the modified T7 promoter. Recognition and subsequent ubiquitination of the mock substrate by the evolved E3 ligase leads to the expression of mock _gIII_. Consequently, the phage offspring are not able to propagate further. Figure created with BioRender.com.
</figcaption>
</figure>

### Assembling the PACE system
To implement this system, we split the evolution process across three plasmids. The first plasmid is the selection phage (SP), which carries the SIAH1/2 gene and the phage genome but lacks the _gIII_, preventing the phage from propagating without the ligase’s activity. The second plasmid, accessory plasmid 1 (AP1), contains the genes for the E1 and E2 enzymes (which are required for ubiquitination but not normally present in bacteria), the N-terminal half of RNAP fused to ubiquitin, and the gIII controlled by the T7 promoter. The third plasmid, accessory plasmid 2 (AP2), contains the substrate fused to the C-terminal half of RNAP.

This modular system allows us to easily swap out the substrate on AP2, enabling it to be applied to different E3 ligases or substrates. It also supports performing “substrate walks,” a process where we incrementally alter the amino-acid sequence of the substrate recognition motif to shift from a canonical target to a novel target of therapeutic interest. By doing this stepwise, we can control the selection pressure and gradually evolve SIAH1/2 to recognize new substrates.

We plan to run this system in a bioreactor to create a continuous evolutionary environment. SIAH1/2 variants that successfully ubiquitinate the changing substrate will enable phage propagation, while less efficient variants are washed out (Figure X below). Over time, we can evolve SIAH1/2 to target a novel substrate, potentially demonstrating that directed evolution is a viable strategy for developing highly specific E3 ligases capable of precise targeted protein degradation.

<figure markdown>
![Figure_positive_negative_selection](https://idec-teams.github.io/2024_Evolution_Suisse/img/PACE_related_schematics/Complete_E3_PACE.png)
<figcaption> Figure X: E3 ligase PACE evolutionary system. The PACE system operates within a lagoon with a constant inflow of new host cells and an outflow of phages and infected host cells. Upon infection of a host cell with a selection phage carrying a functional E3 ligase variant (green arrows), the E3 ligase ubiquitinates its target, which is fused to the C-terminal subunit of a split T7 RNA polymerase (RNAP), using ubiquitin fused to the N-terminal subunit of the split RNAP. The ubiquitin-mediated proximity of the split RNAP subunits assembles a functional T7 RNAP, which transcribes the _gIII_ gene required for the assembly of infectious progeny. In the case of a non-functional E3 variant (red arrows), the lack of assembled T7 RNAP prevents gIII expression, resulting in non-infectious phage progeny. During phage genome replication, the mutation plasmid MP6 increases the mutation rate, generating new E3 variants in the process. Infectious progeny carrying new E3 variants then go on to infect fresh host cells, repeating the cycle.
</figcaption>
</figure>



## Experimental results

### Is phage propagation dependent on the selection phage? 
We tested if the E3 ligases SIAH1 and SIAH2 can trigger phage replication when a specific target protein is present. We used the protein EGLN3, which is known to be recognised by SIAH1 and SIAH2. We attached EGLN3 to part of the T7 RNA polymerase enzyme and infected cells with a few phages carrying the SIAH1 or SIAH2 gene. We measured the amount of phage produced after incubating the cells overnight. The phages carrying SIAH1 and SIAH2 replicated more than phages with an unrelated protein. This experiment indicates that our system worked.


<figure markdown>
![Figure_initial_difference](https://idec-teams.github.io/2024_Evolution_Suisse/img/result figures/Fig1a_wiki.png)
<figcaption> Phages carrying SIAH1 or SIAH2 grow much better than phages carrying an unrelated protein. The fold change shows how much the number of phages increased or decreased (If the number of phages doubles, that is a two-fold increase).</figcaption>
</figure>

We then looked at whether changing the target protein affects phage replication. We replaced EGLN3 (blue) with α-Synuclein (orange), which is also recognised by SIAH1/2. Changing the target protein changes the level of phage propagation. This shows that our system depends on SIAH1 or SIAH2 and the target protein interacting together. 

<figure markdown>
![Figure_initial_difference](https://idec-teams.github.io/2024_Evolution_Suisse/img/result figures/Fig1b_wiki.png)
<figcaption> Phage propagation is dependent on the substrate. The fold change shows how much the number of phages increased or decreased. </figcaption>
</figure>
 

Next, we looked at how changes in the degron would affect our system. We found that even when we altered key parts of the degron in EGLN3, phage replication was not significantly affected. This suggests that phage propagation might be triggered by other factors than the degron. 

<figure markdown>
![Figure_degron_dependency](https://idec-teams.github.io/2024_Evolution_Suisse/img/result figures/Fig1c_wiki.png)
<figcaption> Phage propagation is not affected by the disruption of the degron. The wildtype degron is: FIADVEP. The fold change shows how much the number of phages increased or decreased. </figcaption>
</figure>

We were able to show that phage propagation is dependent on both the substrate of the E3 ligase and the E3 ligase itself. However, we also observed a very high background phage propagation in our system. For our evolution to work, we need to be able to link phage proliferation to degron recognition, so this phage proliferation caused by other factors than the degron interferes with the use of this system for the directed evolution part of this project. The next step is to find out why this is happening and how we can modify our system so that it doesn't happen. 

### What factors lead to unwanted, E3-independent phage propagation? 
We suspected that the background phage propagation we observed could be caused by one of two things: 

1. Leaky transcription of gIII: the gene controlling phage growth is turned on without the split-RNAP components being present. 
2. Spontaneous assembly of the split-RNAP subunits: The two halves of the RNAP are coming together on their own, without the need of ubiquitination of the target substrate.

Both hypotheses lead to gIII expression independent of the E3 ligase activity. To test these hypotheses, we quantified phage propagation in cells that had only one half of the RNAP. In these cells, phage propagation was suppressed, confirming that both halves of the RNAP are required to activate gIII expression. This means that accidental activation of gIII wasn’t the issue. Instead, these results show that the two enzyme halves were probably joining together on their own, causing phage propagation without the involvement of the E3 ligase.

<figure markdown>
![Figure_split_RNAP_parts](https://idec-teams.github.io/2024_Evolution_Suisse/img/result figures/Fig4_wiki.png)
<figcaption> Phage propagation in the presence and absence of split-RNAP components. This figure shows how much the phage population changed after overnight incubation with bacteria missing one of the two halves of the split-RNAP. The results are shown as a log2-fold change, meaning the numbers show how much the phage count increased or decreased, compared to the starting level. NC (negative control) is a bacterial strain lacking both parts of the system. PC (positive control) is a bacterial strain with the full system.</figcaption>
</figure>

### How can we reduce unwanted, E3-ligase independent page propagation? 
We observed that the RNAP enzyme can assemble and become active before the phages even enter the bacterial cells. This early assembly can lead to unwanted phage propagation, which interferes with our goal to link phage propagation to E3 ligase activity. To overcome this problem, we changed the way we control the production of the N- and C-terminal halves of the RNAP. Instead of using a constitutive promoter, which is always active and produces the protein, we switched to a promoter that can be turned on when needed. For this, we chose two different inducible systems. One is switched on by adding vanillic acid (pVan promoter), the other by the stress response caused by phage infection (phage shock promoter). These new systems let us delay the production of the RNAP halves until just before or during phage infection. By regulating when these components are expressed, we can reduce the unintended assembly of the RNAP. This method can easily be added to the PACE system, allowing precise control of the timing of RNAP production.

### Enhancing SIAH1 genetic diversity using drift. 

During PACE, both phages and infected bacteria are continuously removed from the lagoon. If phages propagate too slowly there's a risk that all the phages could be washed out before they can replicate and evolve. This is especially risky at the start of the experiment, when the initial activity of the E3 ligase may be too low to maintain sufficient phage propagation. To mitigate this risk, a process called "drift" is used before the evolution starts. Drift allows random mutations to occur without any selection pressure, increasing the genetic diversity among the phages. This genetic variability helps prevent phage washout by giving the population a better chance of harbouring variants with higher activity that can sustain propagation in the lagoon.

To this end, we propagated the SIAH1 SP phages in bacterial cells that contain a special drift plasmid (DP6). The DP6 plasmid not only increases the mutation rate but also supplies the necessary pIII protein, allowing phages to replicate regardless of the E3 ligase's activity. Over eight infection and growth cycles (called passages), we sequenced the SIAH1 SP phages, and estimated the amount of mutations at different positions in the SIAH1 gene. With each passage, we saw the number of mutated phages increase, creating a highly diverse pool of SIAH1 SP phages. This pool can then serve as a robust starting pool for the next stages of evolutionary experiments, reducing the risk of phage washout and enhancing the chances of evolving phages with improved E3 ligase activity.

<figure markdown>
![Figure_SIAH1_drift](https://idec-teams.github.io/2024_Evolution_Suisse/img/result figures/Boxplot_quality_positions_wiki.png)
<figcaption> Detection of mutated bases in SIAH1-SP during eight drift passages This figure illustrates the accumulation of mutations in the SIAH1-SP gene across eight cycles of drift. Each cycle represents one passage, during which the phages underwent random mutations in the absence of selection pressure. The data demonstrate how much genetic variation has been introduced over the course of the drift passages</figcaption>
</figure>


---
id: 957
title: An in silico approach to modeling Gamma H2AX recruitment of repair proteins in response to double strand breaks
date: 2009-06-04T02:17:59+00:00
author: arisamuel
type: posts
layout: single
guid: http://www.diffusionreactor.com/?p=957
permalink: /in-silico-modeling-gamma-h2ax-repair-proteins-dna-damage
gwo4wp:
  - 'a:4:{s:7:"enabled";s:0:"";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
  - 'a:4:{s:7:"enabled";s:0:"";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
ks_metadata:
  - 'a:7:{s:4:"lang";s:2:"en";s:8:"keywords";s:60:"repair,dsb,gh2ax,process,diffusion,elements,protein,proteins";s:19:"keywords_autoupdate";s:1:"1";s:11:"description";s:155:"repair proteins in response to double strand breaks Akerstein A., Arsuaga, J., Bernstein Initiation of the double strand break (DSBs) repair process begins";s:22:"description_autoupdate";s:1:"1";s:5:"title";s:58:"modeling repair protein movement in response to DNA damage";s:6:"robots";s:12:"index,follow";}'
kdc_metadata:
  - 'a:1:{s:4:"lang";s:2:"en";}'
original_post_id:
  - "957"
categories:
  - Science, Experiments and Technical Stuff
  - Uncategorized
tags:
  - Data Modeling
  - dna repair
---
This was an abstract I submitted for a talk given at the annual &#8216;West Coast Chromatin&#8217; meeting at Asilomar in 2006.

**An _in silico_ approach to modeling** **g****H2AX recruitment of repair proteins in response to double strand breaks**

Akerstein A., Arsuaga, J., Bernstein

Initiation of the double strand break (DSBs) repair process begins with the phosphorylation of the histone variant H2AX (called gH2AX). Deficiency in this process is known to result in genomic instability and thus is fundamental to cellular integrity.

We propose an _in silico_ approach to analyzing the early phase of the repair process whereby gH2AX putatively recruits repair proteins (Rogekau et al. 1998) to the vicinity of the break.

Our goal is to computationally quantify the mechanisms by which gH2AX initiates the DSB response. Using the Gillespie algorithm we establish diffusion parameters and affinity coefficients for chromatin-associated proteins, followed by an analysis of deviations post DSB induction, providing local protein concentrations at DSB loci. Further, this process allows for error evaluation in experimental data.

The ReDi (reaction diffusion) program builds a simulated cell nucleus divided into cubic elements to simulate FRAP (fluorescence recovery after photo-bleaching) recovery curves. Current analyses use the Diffusion equation and are blind to such critical elements of repair as nuclear topology, protein size and concentrations, cellular 3-dimensionality.

Protein coefficients established, we predict how the molecules will interact with other nuclear elements (navigating a chromatin framework for example), to refine our understanding of Gamma H2AX&#8217;s role in DSB repair.
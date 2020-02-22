---
title: "Paper Review: 2020"
author: "HoonTaek Lee"
date: "2020-01-11 15:00:00+09:00"
publishdate: 2020-02-05 11:22:00+09:00
lastmod: 2020-02-22 17:24:00+09:00
draft: false
hideToc: false
enableToc: true
enableTocContent: false
tocPosition: inner
tocLevels: ["h2", "h3", "h4"]
tags:
- Research
- 2020
---

## 11 January, 2020 (Piao, GCB, Phenology)

Piao S, Liu Q, Chen A, et al. Plant phenology and global climate change: Current progresses and challenges. ***Global Change Biology***, 2019;00:1–19. https://doi.org/10.1111/gcb.14619

**Piao et al. (2019) reviewed the current understanding of leaf phenological processes**. They suggested that **four key factors** are driving the phenological processes: 1) temperature, 2) photoperiod, 3) nutrient and water availability, and 4) interseasonal phenological correlations (i.e. the positive spring and autumn phenological intercorrelation).

Temperature regulates periods of endo- and eco-dormancy of leaves. Low temperature stimulates the endodormancy to break; the required amount of accumulated low temperature is numerically represented as a chilling requirement. By the same token, warming is needed to break the ecodormancy before the spring leaf-out. It seems that the amount of the temperature effect differs by circumstances. For example, the warming effect on spring phenology is larger during the daytime than nighttime (Rossi and Isabel, 2017). Also, the spring leaf-out responds less to further warming due to the insufficient chilling accumulation during warmer winters (Fu et al., 2015).

The major effect of photoperiod on leaf phenology is to induce bud set and leaf senescence. However, its effect on spring phenology is still poorly understood. A longer photoperiod with the warmer climate may compensate for the reduced chilling accumulation (Way and Montgomery, 2015), thereby stimulating the spring leaf-out (Chuine et al., 2010). On the other hand, it is also possible that the photoperiod prevents too early leaf-out in spring by reducing sensitivity to warming (Flynn and Wolkovich, 2018).

Sufficient nutrients during the growing season prepare trees well for the freezing stress, postponing the autumn senescence (Sakai and Larcher, 1987). Elevated atmospheric CO2 concentration may also delay the timing of leaf senescence because it enhances water use efficiency of trees and prevents the water stress that causes earlier leaf fall (Reyes-Fox et al., 2014). Water availability also influences leaf phenology. 

Precipitation may be a key factor determining the spring and autumn phenology (Fu et al., 2014, Liu et al., 2016). The snowmelt stimulates root development in spring, leading to leaf flushing (Yun et al., 2018). Water availability may also be linked with the effect of a nutrient on phenology because plants uptake nutrients and water at the same time by their roots. 


## 21 January, 2020 (Brugnera, GCB, Liana)

di Porcia e Brugnera, M, Meunier, F, Longo, M, et al. Modeling the impact of liana infestation on the demography and carbon cycle of tropical forests. **_Global Change Biology_**, 2019; 25: 3767– 3780. https://doi.org/10.1111/gcb.14769

- **Question**:

  1. How much does integrating lianas into the ED2 influence the estimates of forest carbon cycle?

  - The authors **hypothesized** that the impact of lianas on carbon uptake by forest would be **larger in the secondary forests** than in the old-growth forests since lianas showed high density in young forests.

- **Context**:

  - **Lianas (woody vines) have been proposed** as a possible cause of tropical forest structural changes, which limits our understanding of how tropical forests respond to perturbations and quantifying their contribution to the global carbon cycle.
  - **Despite** the demand for inclusion of lianas in models, no single dynamic global vegetation model so far includes lianas.
  - **ED2 is a suitable model** for examining the influence of lianas on carbon cycle because the density of lianas changes with the succession stage of the forest, which demography models take into consideration.

- **Answer**

  1. Liana negatively affected the above ground biomass of early- to mid- successional trees and favored shade-tolerance trees.
     - These were because lianas were treated as a pioneer and light-demanding species in ED2.
  2. The effect of introducing lianas was correlated with liana density.

- **Implication**:

  - Liana could influence the carbon cycle and the structure of forests, although this paper included some debatable assumptions and had limited observations on lianas.

- **Unanswered**:

  - How does **drought stress** affect the simulation results with lianas?
    - ED2 used in this study could not consider the water stress effect (and below-ground competition between different growth forms).
  - **More data** on lianas are needed. For example, lianas display a variety diversity of growth forms, climbing mechanisms, dispersal types, leaf photosynthetic properties, and allocation patterns.

- **Comment**: 

  - The authors did a great job for incorporating lianas into the ED2 with careful considerations of allometry, light competition, and demography.
  - The lianas brought a large change in above ground biomass because the authors assumed that lianas less allocate biomass to their stems. However, **this assumption may not be true**; Smith‐Martin et al. (2019) explained that **mature lianas and trees had a similar proportion of biomass investment to stems** and comply with the same allometric scaling law. This contradictory result may introduce wholly different results to the simulation with lianas.
  - **I like** the opening of the discussion; it say **the value of the modeling experiment**: to enable to investigate the effect of a treatment on variables which are usually not or cannot measured.
  - Also, this study indirectly showed that **abundant measurements are indispensable** for formulating and parameterizing the model; the authors had difficulties in determining the characteristics of lianas such as climbing mechanism and biomass allocation.

## 4 February, 2020 (Jung, Nature, Compensatory)

Jung, M., Reichstein, M., Schwalm, C. et al. Compensatory water effects link yearly global land CO<sub>2</sub> sink changes to temperature. ***Nature*** 541, 516-520 (2017). https://doi.org/10.1038/nature20780

- **Question**:
  1. How do changes in temperature and water availability effect on gross primary productivity (GPP), terrestrial ecosystem respiration (TER), and net ecosystem exchange (NEE) at local and global scales?
- **Context**:
  - **Despite** temperature is known to contribute to the inter annual variation (IAV) of the terrestrial carbon cycle, several studies propose that **water availability play an important role** in the carbon cycle relates such as the carbon balance of semi-tropics and the sensitivity to IAV.
  - An understanding of the process behind **the climatic control of terrestrial carbon cycle** on interannual timescales and across spatial scales is **still lacking**.

- **Answer**
  1. At local scale (grid cell, ~ 50 km), water availability is the major driver of the IAV in GPP, TER, and NEE.
     - Temperature also have amplifying effect on NEE, but the magnitude is negligible.
  2. At global scale, temperature becomes the dominant driver of the IAV in GPP, TER, and NEE.
     - There seems **a local compensation mechanism**: Local variability in GPP and TER compensate locally, dampening water-driven NEE variability
     - There are **spatial compensations**: Spatial variability in water availability also compensates.

- **Implication**:
  - This study **reconciles** existing seemingly contradictory conclusions many studies (i.e. temperature vs water availability)
  - The apparent temperature-dominated IAV of the residual land sink **contains little information on local carbon-cycle processes**
  - The **spatial covariation of climate variables** drives the integrated global carbon-cycle response, as well as local one, and perhaps even **the strength of climate-carbon cycle feedbacks**.

- **Unanswered**:
  - Why temperature contributes little to the local-scale GPP and TER?
  - How does the local **compensation mechanism** occur?
    - The authors guessed that **the concomitant positive relationship** of soil moisture with productivity and with respiration was it (i.e. Both GPP and TER increase with SM, remaining NEE unchanged).
    - Then, **what are the differences** **between high GPP and TER** under pleasing SM condition **and** **low GPP and TER** under harsh SM condition? 
  - Is not there any mechanism that **offset the temperature effect**? **Does it make sense** that the temperature effect at global scale **remains without compensation**?

- **Comment**: 
  - Can we be sure that the water availability hardly affect the global scale productivity? Are there any other ways?
  - It is interesting and encouraging that the TRENDY results generally match those from FLUXCOM data although TRENDY showed under-/over-estimation to a certain degree.
  - It is also interesting how the authors took steps to solve their question and how they deal with the large set of locally gridded and global-scale data.
  - They suggested some explanations for their results, but it seems that this study **created many questions unsolved**, which values this study.

## 7 February, 2020 (Reichstein, Nature, Deep learning)

Reichstein, M., Camps-Valls, G., Stevens, B. et al. Deep learning and process understanding for data-driven Earth system science. ***Nature*** 566, 195–204 (2019). https://doi.org/10.1038/s41586-019-0912-1

- **Question**:
  1. How have machine learning algorithms, especially deep learning, been applied to Earth system science and what is the future direction of the application?
- **Context**:
  - Our ability to produce a deluge of data outpaces our ability to assimilate the information.
  - The advance in computing system, statistical and machine learning modeling have combined with the plethora of Earth system data to create a new avenue of modeling: deep learning. 

- **Answer**
  1. Machine learning approach (such as deep learning) have successfully been applied to many problems in Earth system science.
  2. Machine learning and the physical models can complement each other, creating a new way of modeling: **hybrid modeling.**
  3. **Strengths of the hybrid modeling**
     -  Improving parameterizations: finding optimal values and pertinent patterns (e.g. using ML-derived parameters instead of the pre-defined PFTs).
     -  Replacing a physical submodel; many submodels are of semi-empirical, where the functional form has little theoretical basis.
     -  Analysis of model-observation mismatch: ML can help to identify, visualize, and understand the patterns of model error, which allows us also to correct model outputs.
     -  Constraining submodels
     -  Surrogate modeling: ML can be used for faster simulation.

- **Implication**:
  - Deep learning and other ML algorithms have promising potential to be used for Earth system science.
  - Hybrid modeling, which integrates physical- and data-driven modeling, is recommended.

- **Unanswered**:
  - -

- **Comment**: 
  - **Bayesian framework** is effective in quantifying uncertainties or in tracing the propagation of them.
  - I think that **Reichstein is a great writer**.
  - deluge, soothsaying, pertinent, notwithstanding, yet, tedious, exemplify, ad hoc, circumvent,

## 15 February, 2020 (Ogle, CHANCE, SAM)

Kiona Ogle & Jarrett J. Barber (2016) Plant and Ecosystem Memory, CHANCE, 29:2, 16-22, DOI: 10.1080/09332480.2016.1181961



- **Why did I read this paper?**

**It is often easier to get knowledge** (i.e., model, concept, equation, and so forth) not from the original descriptive paper, **but from other papers using the knowledge** because they introduce the knowledge after masticating it, not as it is.

This paper masticates **the stochastic antecedent modelling (SAM) framework** for beginners. This study describes what SAM does and how SAM does it, and why SAM does it with a simple example and without complicated equations. Whereas, the original paper (Ogle et al., 2015[^1]) provides in-depth explanation about the SAM, but the mathematical expressions cover here and there, making readers terrified even though the two studies exemplified the same case.



1. **Antecedent (or memory) effect**

Antecedent effect (**the effect of the past on current and future plant and ecosystem functioning**) is the key concept gives birth to the SAM. We can see many cases of antecedent effect. For example, in the NBA, a ball handler can break the defender's ankle because the offender's cross-over a few moment ago affects the defender's movement later. By the same token, in a soccer game, the goal keeper can dive into the opposite direction when the ball is refracted because the time when the shooting was made affected the goal keeper, but the time when the ball is refracted has not done yet. In the nature, there are also many processes influenced by conditions in the past (such as photosynthesis, transpiration, leaf flushing, growth, and so forth), but the leverage differs by the timing and variables. Therefore, it is the key to estimate the leverages for each time in the past and variables.



2. **SAM framework**

**SAM estimates the leverage** (the authors used the term "**weights**") **by the Bayesian approach**. The theoretical details and ways to implement this approach are not described in this paper.



3. **Figure 1. Importance of accounting the memory (or weights)**

![](/en/posts/paper_review_2020/2017_Ogle_fig1.jpg)

The authors provides a toy data set which consists of X and Y (**simulated from the X**). When applying the classical regression approach (D.i), it seems that there is only trivial relationships between X and Y (R<sup>2</sup> = 0.07). However, when the memory effect is considered, stronger relationships appear (D.ii ~ D.iv), and the score differs by how the weights for each time assigned (B.i ~ B.iii).



4. **Figure 4. Interpreting the nature' memory effect from weight estimates**

![](/en/posts/paper_review_2020/2017_Ogle_fig4.jpg)

The authors exemplifies a tree-ring growth (G) analysis explained by temperature (T) and precipitation (P) data sets. Monthly weights of T and P were estimated by the SAM and annual weights were given as the sum of 12 month weights of the year. Accorting to the results, P during the winther prior to the growth (probably implies the importance of the snowmelt) and T during summer-autumn transition period of the year before the growth. This shows that G has a longer-term memory for T than for P. As the instance shows, a researcher can verify the existing assumption or draw unexpected implication by weight estimates of SAM.



5. **What's next?**

- How to implement** the SAM framework?: Professor Ogle usually uses R packages.

- **How does Bayesian determine the weights**?

- **For what do I apply the SAM for my research?**

  Possibly, I can apply the SAM for two studies for quantifying the lagged response (or memory effect):

  1) lagged response of fuel moisture content after the end of precipitation

  2) mismatched responses between transpiration (Granier sensor) and net ecosystem exchange (Eddy)

[^1]: Ogle, K., Barber, J.J., Barron-Gafford, G.A., Bentley, L.P., Young, J.M., Huxman, T.E., *et al.* (2015). Quantifying ecological memory in plant and ecosystem processes. ***Ecology Letters***, 18, 221–235.

## 22 February, 2020 (Eller, NPH, JULES-SOX)

Eller, C.B., Rowland, L., Mencuccini, M., Rosas, T., Williams, K., Harper, A., Medlyn, B.E., Wagner, Y., Klein, T., Teodoro, G.S., Oliveira, R.S., Matos, I.S., Rosado, B.H.P., Fuchs, K., Wohlfahrt, G., Montagnani, L., Meir, P., Sitch, S. and Cox, P.M. (2020), Stomatal optimization based on xylem hydraulics (SOX) improves land surface model simulation of vegetation responses to climate. New Phytol. doi:[10.1111/nph.16419](https://doi.org/10.1111/nph.16419)



### Summary

Many researchers, including me, who use ecosystem models have recognized that the beta function approach for representing the change in plant photosynthesis to soil moisture stress needs improvement. In my case, I saw that the ET simulation by JULES was too sensitive to drought, resulting in underestimation. Eller et al. (2020) did a great work for developing an improved alternative method, especially considering xylem hydraulics. By a global evaluation for many biomes, the authors showed that the JULES-SOX outperformed the default JULES for most of evaluations. This improvement spreads out to more accurate estimates of global GPP and ET, predicting plant-physiological response mechanism under the drought condition, the demographic consequences resulted from the more competitive soil moisture use, and possibly replacing the PFT approach in LSMs and DGVMs to represent the large diversity of ecological strategies.



### SOX

**The main hypothesis of SOX** is "stomatal conductance is such as to maximize the product of leaf photosynthesis and xylem hydraulic conductance": maximize{A[ci(gs)] x K[psi(gs)]}

This approach successfully depicts stomatal responses to short- and long-term changes in environmental conditions (i.e., eCO2, soil moisture deficit, and so forth).

SOX estimates of gs is connected to the Collatz model to compute the leaf photosynthesis. 

Whereas, **JULES-default** computes ci using the Jacobs model, and then use the result to compute the leaf photosynthesis using the Collatz model.

Notably, the authors provided **the analytic solution** of the SOX, facilitating easier incorporation to other models and reducing the computing time.



### Other comments

The introduction greatly summarized the history of modelling stomatal conductance.  

CF (Cowan and Farquhar, 1977) - SPA (Williams et al., 1996) - Sperry (Sperry et al., 2017) - SOX (Eller et al., 2018)

CF: maximized A minus the carbon cost of water loss. But the cost of water loss is not linked to measurable variables.

SPA: incorporated plant hydraulics to constrain stomatal optimization, but still relied on a WUE optimization similar to CF.

Sperry: proposed a model that assumes that as xylem hydraulic conductance declines, **the increased risk of hydraulic failure is the main fitness cost** associated with low psi.

SOX: has a different optimization target from that of Sperry: stomata optimize plant dry matter production. In addition, SOX can be solved analytically.
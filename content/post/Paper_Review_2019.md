---
title: "Paper Review: 2019"
author: "HoonTaek Lee"
date: "2019-04-13 15:00:00+09:00"
publishdate: 2020-02-05 11:22:00+09:00
lastmod: 2020-02-05 11:22:00+09:00
tags:
- Research
- 2019
draft: false
---

## 13 April, 2019 (Bonan, ANN, Climate)

Bonan, G. B. (2016). Forests, climate, and public policy: A 500-year interdisciplinary odyssey. **_Annual Review of Ecology, Evolution, and Systematics_**, 47, 97–121.  

I anticipated that this paper explains how the results from forest-climate research have been deployed to public policy. However, this paper had its focus to forest-climate relationships, and "these relationships should be understood well to be properly applied to policy" was all about the public policy. 

Nevertheless, this paper is still interesting enough to read. For me, it was interesing that meteorologist didn't believe that forest affects the climate. Because of this, efforts to investigate forset-climate relationships and include them to climate model were delayed until late 20th century.  

This paper also provides an overview about forest-climate relationships. There are two countered effects. Forest may warm the climate because it has low albedo and emits BVOCs which form aerosol. Conversely, forest may also cool the climate because it accelerates evapotranspiration and turbulent fluxes, and it assimilates atmospheric CO~2~. Interestingly, these effect can vary by spatial and temporal scales. For example, biogeophysical processes (e.g. albedo, ET) are of local to regional scale ones, while biogeochemical processes (e.g. CO~2~ uptake) are of global scale ones. Moreover, it's difficult to predict the effect of local forest cover change on the climate of other region or global climate.  

There are also many papers discuss about forest-climate interaction:  

Bonan, G. (2015). Ecological climatology: concepts and applications. Cambridge University Press.  
Bonan, G. B. (2008). Forests and climate change: forcings, feedbacks, and the climate benefits of forests. **_Science_**, 320(5882), 1444–1449.  
[Popkin, G. (2019). How much can forests fight climate change? **_Nature_**](https://www.nature.com/articles/d41586-019-00122-z)  

Lastly, this paper emphasizes that ESM is a key tool to understand biosphere-atmosphere interaction. 

> "Earth system models provide the single-most comprehensive analysis of biosphere-atmosphere interactions in a variety of contexts."

ESM has many uncertainties and should be cross-validated with other observations such as flux tower measurement and satellite data.

## 20 April, 2019 (Dietze, ANN, NSC)

Dietze, M. C. (2014). Nonstructural Carbon in Woody Plants. **_Annual Review of Plant Biology_**, 65, 667–687.  

NSC is important for tree plants because it acts as an physiological insurance budget for them. I expected that this paper would be organized as a chapter about NSC in a textbook and I can get basic knowledge about NSC. Although this paper is not organized as I expected, it provides well-summarized review about NSC related research results which contain interesting knowledge about NSC.  

Among the results, it's interesting that source and sink strengths influence NSC allocation and NPP/GPP balance. Also, it's surprising that the amount of NSC spans to four times of foliage C at the forest-stand scale. This implies that when NSC related mechanisms are sufficiently understood to be included in ecosystem models, the effect at global scale can be enormous.   

To realistically formulate NSC module, it would be essential to have sufficient amount of measurement with an unified methodology like flux tower measurement of EC method which forms a global network.    

## 27 April, 2019 (Van den Hoof, JGRBG, JULES)

Van den Hoof, C. and Lambert, F. (2016). Mitigation of drought negative effect of ecosystem productivity by vegetation mixing. **_Journal of Geophysical Research: Biogeosciences_**, 121, 2667–2683.  

This paper conducted an interesting numerical experiment to investigate changes in SMC and Carbon & Water fluxes by vegetation mixing. This vegetation mixing was represented by adjusting PFT cover ratios of grid in the JULES model. Results show that NPP and LE flux were increased and SMC was decreased, especially during drought period. This was because multiple PFTs could better exploit ecosystem resources than the sole PFT does, which was related to differences in niche classified by phenology, WUE, and rooting depth.

The way the authors represented vegetation mixing was very interesting. Similar approach was done by Park et al. (2018)[^1] who varies tile size to represent land surface heterogeneity. I think these expriments are valuable because these are good examples that using ecosystem model to test ecological concept.

In addition to the design, they reasonably interpreted the beneath of the mixing effect. They caught difference in rooting depth between C3 plant and tree species and in phenology between deciduous trees and evergreen trees. Especially, I was impressed by the interpretation which related WUE to the different changes in magnitude by mixing between NPP and LE flux. By pointing out step by step in the timeseries considering WUE and other differences, the authors nicely described why the results came out.

[^1]: Park, J., Kim, H.-S., Lee, S.-J. and Ha, T. 2018. Numerical Evaluation of JULES Surface Tiling Scheme with High-Resolution Atmospheric Forcing and Land Cover Data. **_SOLA_**, 14, 19-24.

## 5 May, 2019 (Xu, NPH, ED-Hydro)

Xu, X., Medvigy, D., Powers, J.S., Becknell, J.M. and Guan, K. (2016). Diversity in plant hydraulic traits explains seasonal and inter‐annual variations of vegetation dynamics in seasonally dry tropical forests. **_New Phytologist_** 212(1), 80-95.

This paper incoporated hydraulic module into the ED2. This module accounted for hydraulic traits such as tugor loss point (TLP), saturated xylem conductivity, 50% xylem conductivity loss water potential, and area-based A~net~ under sufficient water supply. These traits were estimated using a meta analysis in which relationships between the traits and wood density (WD) or SLA were retrieved. Also, four new PFTs, which were classified based on the SLA-WD space, were introduced to the model. And then finally some simulations were conducted to investigate the effect of adding the new module and PFTs by comparing with in-situ observation and MODIS data.

The approach the hydraulic module used was attractive. The hydraulic traits of each PFT could be naturally and separately considered. This consideration will improve simulations for carbon and water and especially ones under drought condition. Also, it was interesting that the model could show the contribution of night time transpiration to restoration of tree water storage. On the other hand, the relationships between the four traits and WD or SLA seem to need improvement. This improvement may improve the model performance. In addition, by comparing the models before and after incoporating the improvement, the contribution of the relationship to the simulation will be quantified and some meaningful functions of the traits to ecosystem may be drawn.

## 11 May, 2019 (Zhang, JGRBG, CLM4.5)

Zhang, L., Lei, H., Shen, H., Cong, Z., Yang, D. and Liu, T. (2019). Evaluating the representation of vegetation phenology in the Community Land model 4.5 in a temperate grassland. **_Journal of Geophysical Research: Biogeosciences_** 124.

This was a key paper for the first revision of my paper. This paper had its focus on improving phenology module in CLM 4.5 by comparing MODIS LAI. Two problem were issued and resolved. **First**, EOS in the CLM 4.5 was too late compared with that of MODIS LAI. The authors showed that too low threshold soil temperature for leaf offset caused this problem; the temperature was increased. **Second**, the model sometimes showed zero LAI during summer, which caused multiple growing cycles. This problem was resulted from too high rate of leaf onset. By adjusting the rate, this problem could be solved. And then the authors confirmed that how these improvements affected GPP and ET simulations at stand and national levels.

For me, it was impressive how the authors found the causes of the two problems. They thoroughly investigated the sensitivity of the model to some parameters relevant to the problems. And they analyzed the test results concerning the internal processes of the model. On top of that, the discussion about applicability of the modified model was well written. The authors classified temperate grassland and characterized them in terms of their phenology drivers. Based on the properties they judged which type of grassland the model can be applied to.    

## 18 May, 2019 (Fisher, ANN, TBM)

Fisher, J.B., Huntzinger, D.N., Schwalm, C.R. and Sitch, S. (2014). Modeling the terrestrial biosphere. **_Annual Review of Environment and Resources_**, 39, 91-123.

This paper synthesized in what context the terrestrial biosphere model (TBM) appeared, which processes TBMs included, and what's next. It was interesting that actually many part of the TBM was studied and developed separately around the world, and the development was accelerated after the parts were incorporated into a type of model.  

On top of that, there was about the JULES and ED. JULES deveolopers were proud of the structure and quality of the way it's source code. About the ED, it seemed to be valuable because the ED can simulate the heterogeneity of PFT composition in detail, which should depend on resource allocation equations or be simplified. Quillet et al. (2010)[^2], which is also a nice review paper of DGVM, agreed with this perspective. They described that ecosystem demographic modules such as ED can replace the PFT concept and resolve problems of it to a certain degree.

[^2]: Quillet, A., Peng, C. and Garneau, M. (2010). Toward dynamic global vegetation models for simulating vegetation–climate interactions and feedbacks: recent developments, limitations, and future challenges. **_Environmental Reviews_**, 18, 333-353.

## 26 May, 2019 (Li, GCB, SIF)

Li, X., Xiao, J., He, B., Altaf Arain, M., Beringer, J., Desai, A.R., Emmel, C., Hollinger, D.Y., Krasnova, A., Mammarella, I., Noe, S.M., Ortiz, P.S., Rey-Sanchez, A.C., Rocha, A.V. and Varlagin, A. (2018). Solar-induced chlorophyll fluorescence is strongly correlated with terrestrial photosynthesis for a wide variety of biomes: First global analysis based on OCO-2 and flux tower observations. **_Global Change Biology_**, 24(9), 3990-4008.

This paper demonstrates that SIF is a strong proxy of terrestrial GPP using different point of view. Also, it shows that SIF is more strongly correlated with GPP than VIs (EVI, NDVI) and GPP estimates from LUE methods.  

GPP estimation using SIF from satellites is relatively new method, which started about a decade ago. But, it seems a very strong method because SIF can response sensitively to physiological changes in plants. Also, SIF method is becoming more powerful because SIF data from satellites is available. Moreover, the utility of the data will be better as the spatial resolution of the data will be finer.  

This method is a representative example of the potential of RS. Everytime a new algorithm for a new variable is added to satellites, satellite will observe the variable in a planet-scale scope. In addition, this method is a great example of application of physiological mechanism to the remote sensing algorithm.  

## 8 June, 2019 (Hartmann, NPH, Mortality)

Hartmann, H., Moura, C.F., Anderegg, W.R.L., Ruehr, N.K., Salmon, Y., Allen, C.D., Arndt, S.K., Breshears, D.D., Davi, H. and Galbraith, D. (2018). Research frontiers for improving our understanding of drought-induced tree and forest mortality. **_New Phytologist_**, 218(1), 15-28.  

This paper suggests some research frontiers (questions) about plant responses to drought. But, rather than the suggestions, I was interested in the topic of Box 1: definition of death for plants. Plants are different to animals, physiologically. Plants lack the nervous system, can easily resprout from a organ, and maintain their lifes with only a few parts of them. These features make a complex issue in defining the death of plant, and this propagates to a hardness in understanding and predicting plant motality.  

Another one I want to point out is that it would better to cite the paper by Xu et al. (2016) when the authors argues a need for incorporating plant hydraulic schemes to DGVMs. This is because it is a well-structured paper and it used a novel approach of representing the plant hydraulics so that the ED model can consider the scheme of every PFTs it contains.

## 15 June, 2019 (Berry, pce, FWU)

Berry, Z.C., Emery, N.C., Gotsch, S.G., Goldsmith, G.R. (2019). Foliar water uptake: Processes, pathways, and integration into plant water budgets. **_Plant, Cell and Environment_**, 42, 410-423.   

As I saw foliar water uptake (FWU) in alert lists sometimes, I became curious about the process. So I read this paper. FWU was observed about 400 years ago (1727), but it seems like relatively new and immatured field. Some knowledge chunks have been made, but the field lacks many details. Roughly, FWU occurs when leaves are wet, the main gate of water movement is stomata, most of biomes shows this phenomenon, and the amount is up tp 10% of transpiration. But, further studies such as details about water movement, methodologies to observe the pathway, and species-specific physiological responses.  

Interesting points are: 1) sap flow measurement can contribute to this field by measuring and quantifying whole-plant scale FWU. Stable isotope method can be applied to track the water movement. Also, hydraulic traits related with the FWU need to be investigated. All these fields are among the interests of my previous lab. So, FWU might be a potential research candidate for the lab (it seems deserved). 2) FWU improves leaf water status when plants suffer drought although it occupies just a small part of the plant water fluxes. This is an important point because drought is one of the major concerns of forest science. FWU may be a game changer for plants during dry condition.  

## 22 June, 2019 (Vinodkumar, AFM, SMC)

Vinodkumar and Dharssi (2019). Evaluation and calibration of a high-resolution soil moisture product for wildfire prediction and management. **_Agricultural and Forest Meteorology_**, 264, 27-39.   

This paper can be a good guide for both of my researches at SNU and NIFOS. This paper used the JULES to predict soil moisture deficit (SMD), which is similar to the object of the study at SNU. On the other hand, the purpose of SMD prediction was to imporve a fire danger index, which is the same as my research at NIFOS.  

This study is superior to mine with some reasons. One of them is that the correlation coefficient between the simulated soil moisture and measured one was usually larger than mine (0.7 vs 0.63) although both estimation were based on the same land surface model. I need to investigate the reason to increase my r values. Whereas, there are also some deficiencies. The spatial resolution is coarser than mine (5 km vs 810 m) and the localization of the JULES is done with more depth in my research at SNU.  

As comparing with my research in NIFOS, I can go further a step because this study produced SMD as a substitute of fuel moisture content (FMC) while I am aiming to model the FMC directly and I will produce spatial distribution of FMC in the end.  

## 12 August, 2019 (Resco, AFM, FMC)

Resco de Dios, V., Fellows, A.W., Nolan, R.H., Boer, M.M., Bradstock, R.A., Domingo, F. and Goulden, M.L. (2015). A semi-mechanistic model for predicting the moisture content of fine litter. **_Agricultural and Forest Meteorology_**, 203, 64-73.   

I read this paper to get some hints for my fuel moisture research at NIFOS. This paper developed a semi-mechanistic model in which fuel moisture content (FMC) and vapor pressure deficit (VPD) were exponentially related. This model is able to be easily applied to other researches once VPD for target sites is known. Hence, contrary to my model, this model can be synergized with remote sensing VPD data sets to broaden the spatial scope of the model.  

I contemplate that I can include this model to compare with other models in my on-going paper. Also, it looks also a good idea to analyze additionally the model performance for lower FMC range because my research results will be incorporated to the fire danger rating system of NIFOS. On the other hand, FMC model of this paper poorly estimates FMC during late autumn and winter, and steadily underestimates the maximum FMC even it works well for other seasons. This result is also curious.




##  7 December, 2019 (Bar, NPH, Fire)

Bär, A., Michaletz, S.T. and Mayr, S. (2019), Fire effects on tree physiology. **_New Phytologist_**, 223: 1728-1741. doi:10.1111/nph.15871

My research group at NIFOS was invited to write a research paper for a special issue of a journal. We decided to write a paper about the lagged browning after the forest fire at April 2019. I wrote about how forest fire affects an individual tree's physiology, referring majorly to this paper.  
This paper, as other Tansley reviews often do, includes excellent visual summaries like Figure 3 which compiles the physiological responses of plant organs to fire injuries. In short, dreadful heat and drastic drying are the major causes of burning up NSCs, malfunctioning of the hydraulic system, and increasing susceptibility to insect attacks.
After reading this,  I felt that the mechanism behind the fire-caused tree dieback is the same as the one behind general tree dieback. Fire is just one of the triggers.

## 17 December, 2019 (Smith-Martin, NPH, Liana)

Smith‐Martin, C.M., Xu, X., Medvigy, D., Schnitzer, S.A. and Powers, J.S. (2019), Allometric scaling laws linking biomass and rooting depth vary across ontogeny and functional groups in tropical dry forest lianas and trees. **_New Phytologist_**. doi:10.1111/nph.16275

- **Question**:
  
  1. Do mature lianas invest less biomass in stems compared to trees? The authors tried to compare the investment strategy between lianas and trees.
  2. Do juveniles follow the same allocation patterns as mature individuals?
  3. Is either leaf phenology of life form a predictor of rooting depth?
  
- **Context**:
  - The number of Lianas are increasing and it is needed to examine their influence on the ecosystem and global climate (e.g. C cycle) 
  - Plant biomass partitioning and rooting depth play pivotal roles in both ecological theory (APT: a constant allocation vs OPT: dynamic allocation in cope with resource limitation) and in ecosystem simulation models (phenology, WUE, ...).
  1. Lianas may invest less biomass to stems and more to roots and leaves because they use trees for mechanical support.
  2. The biomass allocation pattern by age is unknown.
  3. There have been conflicts on lianas' rooting depth because of lack of *in-situ* survey. why did the authors try to estimate the rooting depth?
  
- **Answer**
  
  1. Mature lianas and trees showed similar proportion of biomass investment to stems. **That is, mature lianas and trees abide by the same allometric scaling law.**
  2. No. Juvenile lianas, deciduous trees and evergreen trees had a different allocation pattern while mature lianas showed a similar pattern with that of surrounding trees.
  3. Lianas were not deeper-rooted than trees. Evergreen trees had the deepest roots to maintain canopy during dry season. 
- **Implication**:
  
  - The biomass allocation pattern of lianas changes with its age. So, it cannot be estimated from a few experiments and more researches are needed.
  - Rooting depth differed by the life form (lianas < deciduous trees < evergreen trees)
  
- **Unanswered**:
  - How lianas maintain similar or better water status and grow more during seasonal drought?
  - How co-occurring trees of lianas grow more during the wet season in semi-moist forest?
  - Do lianas and trees have different amount of fine root biomass?

- **Comment**: This study is one of the leading studies that try to incorporate lianas into the ecosystem model. The results of this study are quite robust as they are based on a large dataset from *in-situ* survey including harvesting with well-organized factorial experiment design and relevant statistical methodologies. This data and ED2 were examined by each other. In sum, this study a well-done work given a unique context (Lianas), focused questions, well-organized experiment design, proper analyzing ways coping with corresponding questions, and applying a terrestrial ecosystem model. 

## 18 December, 2019 (Fisher, NPH, JULES-ED)

Fisher, R., McDowell, N., Purves, D., Moorcroft, P., Sitch, S., Cox, P., Huntingford, C., Meir, P. and Ian Woodward, F. (2010), Assessing uncertainties in a second‐generation dynamic vegetation model caused by ecological scale limitations. **_New Phytologist_**, 187: 666-681. doi:10.1111/j.1469-8137.2010.03340.x

- **Question**:
  1. How demographic processes of two-dimensional spatial scales influence simulations of community structure, and responses of ecosystems to climate change?
  
- **Context**:
  - Recently second-generation DGVMs have become advanced in their capability to simulate short-term surface gas and energy exchanges and atmospheric CO<sub>2</sub>.
  - However, the 2<sup>nd</sup> gen. DGVMs are still lack in representation of demographic processes because of insufficient observations.
  - This poor representations of competition and coexistence may bring uncertainties in simulation of the community structure and responses of ecosystem to climate change.
  
- **Answer**
  1. Varying the five unconstrained parameters (seed advection, seed mixing, sapling survival, competitive exclusion, and plant mortality) **introduced diverse predictions of community structure** ranging from monocultures to equal co-dominance of the seven PFTs.
  2. When exposed to a climate change scenario, the competing impacts of CO<sub>2</sub> fertilization and increasing plant mortality **caused ecosystem biomass to diverge substantially** between simulations.
  
- **Implication**:
  - Demographic processes represent a large source of uncertainty in DGVM predictions.
  
- **Unanswered**:
  - Examining the uncertainties caused poor representations of demographic processes by top-down approach

- **Comment**: 
  - The uncertainties from demographic processes may show an interaction effect with other uncertainties (e.g. NSC, hydraulics, phenology, nutrient ...).
  - Attaching another module explicitly seems like a great way of preliminary test.

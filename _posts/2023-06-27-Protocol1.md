---
layout: post
author: MBM
---

Protocol for the Alejandro's data, complete reactions.

1. Use 1_getComplete_SSrxnReagProd_wPubYearJP.awk
   This script takes each ID reaction and extracts the reagent and product. The reactions have to be single step and is only considered complet reactions, this means that it should to exist at least a reagent and a produt. The input data is the preprocessed data done on August 28 2022. This data is stored on /scr/k70san2/marisol/P_RXN/scr_28_Aug_22. The output data is a .tsv file with five columns: RXN_ID, participant substances, years of publication in journals and patentes, years of publication in journals and years of publication in patentes.

2. Use 2_birthYearPubJP_complete_SSrxnReagProd.awk
   This script finds the first date of appearance of every reaction reported in the reaction context, considering all the reaction details, published in patents and journals. The input data comes from 1_getComplete_SSrxnReagProd_wPubYearJP.awk outpu data. The output data is a  .tsv file with trhee colummns: RXN_ID, substances involved (reagents and products) and the first year of  appearance between journals and patents.

3. Use  3_Join_density_distri_no1800.py
   Once we have the reactions with the substances involved and the year of first appearance, we use this script to obtain  two set of data:
   1. Dist_tablas_*year*.tsv -> in the *year* number of new reactions with differnt size. The output is a table with the number of reactions vs size (number of substances involved). This is not cumulative. The tables has the following form (2016):
      Num_subs		     Num_rxn
      3					511283
      That means that in 2016 there were published 511283 reactions with three substances involved.
   2. tablas_*year*.tsv -> in the *year* , the number of substances that partipates in how many reactions. This is cumulative. The tables has the following form (2016):
      Num_rxn		Num_subs
      1			8703902
      That means that until 2016,  8703902 substances had been published, participating in only one reaction.


Then, we have to deal with the non conected and conected substances.

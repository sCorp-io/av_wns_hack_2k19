## av_wns_hack_2k19
https://datahack.analyticsvidhya.com/contest/wns-analytics-wizard-2019/

Code/Approach for 46th place solution on the private LB for the wns analytics wizard 2019 hackathon hosted by Analytics Vidhya.

#### Dependencies:
  * python
  * numpy
  * pandas
  * scipy
  * sklearn
  * catboost
  
  
  ### Approach
  
  #### Validation set: 
  All the impressions after **2018-12-09** are used as the validation set.
  As small gains in AUC on this validation set improved performance on the public LB
  
  #### Features:
  Following features were used:
   * **TSL Ad** - Time since last ad
   * **Nth impression count** - The number of times ads are shown to a given user
   * **Time features** - Features like day of the week, hour of the day etc
   * **Historical statistical features** - Ex: num_uniq_items, item_price_mean etc
   * **category type wise counts** - for cat_1, cat_2, cat_3
   * **stat features for session and time**
   
Decided to go with catboost here, and tried converting few categorical features to continuous
The number of bins for each continous feature was decided using freedman_diaconis
Intially the best iteration was found using validation data
To generate the final submission a full pass over the train data was made using this best_iter


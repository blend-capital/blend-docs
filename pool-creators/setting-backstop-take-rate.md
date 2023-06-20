# Setting Backstop Take Rate

The Backstop Take Rate is the percent of interest paid by pool borrowers that is sent to the pool's backstop module depositors. The level it's set at governs what proportion of capital you can expect the backstop module to have in relation to the pool. This correlation is a result of a higher backstop take rate making depositing in the backstop module more profitable in comparison to lending to the pool.\
\
Here are example backstop take rates for pools of various risk levels using the following formula

$$BackstopInterestRequirement = RequiredTVLCoverage*RequiredInterestMultiple$$\
$$BackstopTakeRate = \frac{BackstopInterestRequirement}{(1+BackstopInterestRequirement)}$$

#### Low Risk Pools

* Assumptions:
  * Need 2% of TVL covered
  * Backstop depositors demand a rate of 2.5x the lender's rate
* Required take rate of 4.75%
* Compound V3 would be considered a low risk pool

#### Medium Risk Pools

* Assumptions:
  * 7.5% of TVL covered
  * Backstop depositors demand a rate of 4x the lender's rate
* Required take rate of 23.508%
* Aave V2 would be considered a medium-risk pool\


#### High Risk Pools

* Assumptions:
  * 15% of TVL Covered
  * Backstop depositors demand a rate of 5x lender's rate
* Required take rate of 42.86%
* Most pools with Stellar native tokens should be considered high risk

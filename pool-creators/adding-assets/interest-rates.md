# Interest Rates

Interest rate parameters are used to define how much borrowers should be charged for borrowing assets at different utilization rates.

Utilization Rate

An asset's utilization rate is the percentage of the asset's deposits that are currently being borrowed. It can be calculated using the following formula\
U = D/T

Base Interest Rate

An assets base interest rate is dynamic - it's based on a three tier utilization curve which is made by setting the following parameters

Target Utilization

The target percentage of an asset’s supply that should be borrowed. This should be set high for assets that are intended to be borrowed and lower for assets that are intended to be used as collateral.&#x20;

Rate Slope 1

The rate at which an asset's borrowing interest rate increases when it's below it's target utilization

Rate Slope 2

The rate at which an asset's interest rate increases when it's above its target utilization

Rate Slope 3&#x20;

The rate at which an asset's interest rate increases when it's above 95% utilization. An asset should never be above 95% utilization as it causes liquidity issues for lenders, thus, this slope should typically be set fairly high.

Base Interest Rate Equation\


$$
IR(U)= \begin{cases} (R_{base}+\frac{U}{U_T}R_1) & \text{if } U\leq U_T\\ (R_{base}+R_1+\frac{U-U_T}{0.95-U_T}R_2) & \text{if } U_T\lt U\leq 0.95\\ (R_{base}+R_1+R_2)+\frac{U-0.95}{0.05}R_3 & \text{if } 0.95\lt U\\ \end{cases}
$$

Sample base interest rate graphs

Low utilization asset, target utilization = .5, R1 = 0.05, R2 = .25, R3 = .5  \
\
![sss](https://lh6.googleusercontent.com/AABlUmMi\_qP-T869DiVoWBPDK3kvPDw4wgge2zvfDZA1zpMZZTLPC5tXWmkoAP34LbP5ZCVF1LJC-9AQxBOyuggwvg5ovcKqY14OVSa\_kBfwsH7-SiujAiFjsZW8si\_aGTp0uQ9Hs7nnBu19a4bB8lI)

High utilization asset, target utilization = .85, R1 = .05, R2 = .15, R3 = .5

![](https://lh4.googleusercontent.com/rUWeKC6RUCHTnWW22aHq3E9iJej-aG-pU8l93pSonLge953ePR1TU3sRwCkakJWKP1JWdES9j9Ntvd4esx-Zx2WOuNEQUlC0GtmvMiOMMRhnqEmELyQhUbWddPNpW80wAQekHPUJaYqDvF79Q4DnN3c)

Fixed rate asset, target utilization = 0.01, R1 = .05, R2 = 0, R3 = 0

![](https://lh3.googleusercontent.com/x2k\_vSDZdHqXGfzHUwxbdEGHDrXH6c1Kt49UDxHCoq-47wLWrvXoAoeaBgJgDAqWWbzBzUgDqfVQ\_3bP83u-0BjE-BEowBF5DQgH0UP4v\_NcYWnippq-vexh1FfaMf\_-8e6ytFRIlVMbWqpZtjRBV48)

Rate Modifier

In addition to being dynamic, interest rates are reactive. When an asset is below its target utilization, its interest rate will gradually decrease. When it’s above, the interest rate will increase. Target utilization should be set high for assets that are intended to be borrowed, like USDC, and low for assets that are designed to be primarily used as collateral.

This serves to ensure that capital remains efficiently allocated between BLND lending pools.

The rate modifier equation is

$$
\ Rate Modifier = Util Rate Error * Reactivity Constant + Rate Modifier
$$



UtilRateError

The utilization rate error is the accumulation of how far off an assets utilization rate was from it's target

$$
Util Rate Error = \Delta blocks * (U_T-U)
$$

Reactivity Constant

A value that governs how quickly interest rates adjust based on assets target utilization. This should be set based on how quickly users are expected to react to market inefficiencies. Additionally, it should also be set higher for assets with high-utilization targets to prevent them from experiencing excessive rate volatility, and lower for low-utilization target assets.&#x20;

For example, a reactivity constant of 0.0000002 will cause interest to approximately double in 2 months if the utilization rate is steadily 10% higher than it should be, making it a good choice for high utilization target assets.

518400 seconds \*0.0000002\* .10 error \*10 scaling = 1.0368 +1 = 2.0368&#x20;

The full interest rate equation with the reactivity constant is

$$
\ IR(U)= \begin{cases} RM*(R_{base}+\frac{U}{U_T}R_1) & \text{if } U\leq U_T\\ RM*(R_{base}+R_1+\frac{U-U_T}{0.95-U_T}R_2) & \text{if } U_T\lt U\leq 0.95\\ RM*(R_{base}+R_1+R_2)+\frac{U-0.95}{0.05}R_3 & \text{if } 0.95\lt U\\ \end{cases}
$$

You'll notice that the rate modifier only modifies the first two interest rates, this is because the last rate slope should be seen as an Oh Shit slope with a very high value that assets shouldn't normally venture into. Allowing the rate modifier to affect it would make interest rates too volatile.\
\




&#x20;

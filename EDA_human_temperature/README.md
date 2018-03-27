# Is 98.6 Degrees Optimal? An EDA of Human Body Temperature
#### Given a population sample of 130 body temperatures, what can we infer about the population?
********************************
### Data Inspection

#### Total Sample of Males and Females
* Sample Mean:                     **_x&#772;_** = 98.249231
* Sample Standard Deviation:       **_s_** = 0.733183
* Sample Count:                    **_N_** = 130

#### Males Only Sample
* Sample Mean:                     **_x&#772;_** = 98.104615
* Sample Standard Deviation:       **_s_** = 0.698756
* Sample Count:                    **_N_** = 65

#### Females Only Sample
* Sample Mean:                     **_x&#772;_** = 98.39
* Sample Standard Deviation:       **_s_** = 0.743488
* Sample Count:                    **_N_** = 65

First things of note are that the sample mean, at 98.25<sup>o</sup>, is 0.35 degrees less than the widely expected and accepted mean of 98.6<sup>o</sup>, and that women appear to be naturally hotter than men. To further inspect the latter, we can illustrate this with a swarmplot of the data between males and females:
<p align="center">
  <img src="https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/EDA_human_temperature/images/swarmplot.png">
</p>

# Is the Distribution of the Sample Normal?

When plotting the sample distribution of body temperatures, initial intuition doesn't lean towards the notion that the sample is normally distributed. In fact, when sampling and overlaying the normal distribution using the sample's mean **_x&#772;_** of 98.25 and standard deviation **_s_** of 0.733, the ambiguity intesifies:

<p align="center">
  <img src="https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/EDA_human_temperature/images/normal sample.png">
</p>

It is only when we overlay the sample's Cumulative Distribution Function (CDF) with our sampled normal distribution's CDF do we confirm that it wouldn't be grossly incorrect to assume the sample is **_Normally Distributed_**

<p align="center">
  <img src="https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/EDA_human_temperature/images/cdf.png">
</p>

The same can be said when breaking down the sample into its individual male and female constituents. As seen below, the male only samples almost fit the normal ECDF whereas the female only samples loosely overlay the normal ECDF with slight departures at the lower end of the temperature spectrum and the higher end. Again, it wouldn't be grossly incorrect to assume both the male and female only samples are also normally distributed.

<p align="center">
  <img src="https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/EDA_human_temperature/images/mf_normal_ecdf.JPG">
</p>

For concreteness however, we can perform D’Agostino and Pearson’s **_Omnibus K<sup>2</sup> statistic_** which is a test for departure from normality based on kurtosis and skewness. I won't conver this topic in detail. Instead relegate the reader to do their own reserach [HERE](https://www.jstor.org/stable/2334522?seq=1#page_scan_tab_contents). The **stats** module of the _SciPy_ library allows one to perform this test with one line of code. Maintaining the scope of this EDA, as long as the p-value returned by this test is above 0.05 (within the 95% confidence interval) then we **cannot reject** the null hypothesis:
* H<sub>0</sub>: The sample of temperatures is normally distributed

| Sample | p-value | Result |
| :-------------: |:-------------:| :-----:|
| Males & Females | 0.26 | Normally Distributed |
| Males Only | 0.64 | Normally Distributed |
| Females Only | 0.09 | Normally Distributed |

As you can see the quantitative values back up the qualitative (graphical) notion that the distributions are normal. The Females Only sample however is ever so barely considered normal as the critical threshold was 0.05 and the Females Only p-value is 0.09

### Independence and Sample Size
According to the Central Limit Theorem ---> When independent random variables are averaged, their properly normalized mean **_x&#772;_** tends toward a normal distribution even if the original variables themselves are not normally distributed. The general rule of thumb for this to also hold true is that **n > 30**. The current sample size is 130 with 65 of the temperatures being that of men and 65 being of female. Being that we have already shown the sample is Normally Distributed above, and the sample size **n = 130 >> 30** We can adequately proclaim that the samples are Independent and the Sample Size is sufficiently large enough  to be considered a large sampling of the population.

# Is the True Population Average Temperature 98.6<sup>o</sup>

#### Central Limit Theorem Method Analysis
What the Central Limit Theorem allows us to answer is, when a population with parameters: mean &mu; = X and standard deviation &theta; = Y, is sampled with n samples, what is the probability (the likelihood) that the sample will have mean **_x&#772;_** = Z. Framing this in the context of the current EDA, if the mean temperature of the population is 98.6 degrees what is the likelihood that a sample of n = 130 people from the population will have a mean **_x&#772;_** = 98.25. Since the temperatures are independent of each other, a one sample test is performed. Given that the sample is large with N = 130 and we don't know the standard deviation of the population, we make a best guess assumption that the standard deviation of the sample **s** is representative of, and approximately equal to the standard deviation of the population &theta;. If we were to sample the population 10,000x, each sample size being N=130, and then computed the mean for each of the 10,000 samples, this distribution would be a normal distribution. According to the Central Limit Theorem, the mean **_x&#772;_** of this distribution of sample means would be equal to the mean &mu; of the population. The standard deviation of this distribution &theta;x&#772; would be equal to the standard deviation of the population divided by the square root of the sample size <img src="https://latex.codecogs.com/svg.latex?\inline&space;\frac{\theta&space;}{\sqrt{n}}" title="\frac{\theta }{\sqrt{n}}" />
. Knowing that the distribution of sample means is normal, we can sample the normal distribution using the aforementioned mean x&#772; and standard deviation &theta;x&#772; and then calculate the 95% confidence interval. If our sample's mean of 98.25 is outside this confidence interval, then we **can reject** the null hypothesis that 98.6 is the mean population temperature.
> H<sub>0</sub>: The mean temperature of the population is 98.6<sup>o</sup>

Process
********
* Sample the normal distribution using mean x&#772; = 98.6 and standard deviation &theta;x&#772; = <img src="https://latex.codecogs.com/svg.latex?\inline&space;\frac{\theta&space;}{\sqrt{n}}" title="\frac{\theta }{\sqrt{n}}" />
 = <img src="https://latex.codecogs.com/svg.latex?\inline&space;\frac{0.733183&space;}{\sqrt{130}}" title="\frac{0.733183 }{\sqrt{130}}" /> = 0.064304403
* Calculate the 95% confidence interval for this distribution of means
* If our sample mean is outside of this interval then reject the null hypothesis

After sampling the normal distribution with the given parameters, we get the following distribution

<p align="center">
  <img src="https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/EDA_human_temperature/images/clt.png">
</p>

The 95% confidence interval and interpretation for this distribution is:

> **Because our sample mean of 98.25 is outside of the 95% confidence interval (98.475 - 98.723), what Central Limit Theorem tells us is that it is unlikely that 98.6<sup>o</sup> is the population mean temperature and that we should reject the null hypothesis. Also, from the qualitative graph above, we can see that the probability of even getting a mean temperature of 98.25<sup>o</sup> is extremely close to 0%. This means that if the average population temperature was 98.6, the chance of extracting the sample we have is practically 0%**

#### Boostrap Method Analysis
When performing boostrap analysis of a sample, we treat the sample, as the population and sample it with replacement. In this case, the sample was resampled 10,000x. The mean was calculated for all 10,000 samples and a distribution is plotted with the 95% confidence intervals calculated. If 98.6<sup>o</sup> is outside of this interval, then we reject the null hypothesis:
> H<sub>0</sub>: 98.6<sup>o</sup> is the population average temperature

Process
*********
* Resample, with n = 130, the sample 10,000x and create a distribution of 10,000 means
* Calculate the 95% confidence interval for this distribution of means
* If 98.6<sup>o</sup> is outside of this interval, then reject the null hypothesis

Using this process we obtain a normal distribtuion that looks like:

<p align="center">
  <img src="https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/EDA_human_temperature/images/bootstrap.JPG">
</p>

The 95% confidence interval and interpretation for this distribution is:
> **Because our hypothesis mean of 98.6<sup>o</sup> is outside of the 95% confidence interval (98.121 - 98.375), we should reject the null hypothesis that the population average temperature is 98.6<sup>o</sup>**

##### t-statistics vs z-statistics
t-statistics and t-tests are more prudent to use when the sample size n < 30 or when the population standard deviation &theta; is unknown. When the sample size is greater than 30, z-statistics are the more appropriate metric. However if the t-test is utilized when n > 30, the result will be almost identical to using z-statistics. This can be proven using the stats module from the SciPy library for the t-test. In our case n = 130. We already know the results for the z-statistics as this is the method used for the analysis described above.

|                      | **_z-statistics_** | **_t-statistics_** |
| :------------------: | :-----------------: | :----------------: |
| **_Score_** | -5.468749999999911 |  -5.4548232923645195 |
| **_p-value_** | 2.41e-07 | 2.41e-07 |

To further highlight the affects of sample size on z & t statistics, when taking a random sample of size n = 10 out of our total sample and applying both statistics, we get the following results when we run the experiment 5 seperate times:

|      **_Sample 1_**                | **_z-statistics_** | **_t-statistics_** |
| :------------------: | :-----------------: | :----------------: |
| Score | 1.688 |  -1.602 |
| p-value | 0.045 | 0.143 |
|      **_Sample 2_**                | **_z-statistics_** | **_t-statistics_** |
| Score | 3.454 |  -3.277 |
| p-value | 0.0002753 | 0.00956 |
|      **_Sample 3_**                | **_z-statistics_** | **_t-statistics_** |
| Score | 1.891 |  -1.794 |
| p-value | 0.029 | 0.106 |
|      **_Sample 4_**                | **_z-statistics_** | **_t-statistics_** |
| Score | 1.131 |  -1.073 |
| p-value | 0.128 | 0.311 |
|      **_Sample 5_**                | **_z-statistics_** | **_t-statistics_** |
| Score | 2.420 |  -2.296 |
| p-value | 0.00774 | 0.047 |

From this experiment, we can see that when sample size n < 30, even though the scores are almost equal in magnitude, their p-values vary greatly. This is becuase z-statistics require the distribution to be normal in order to be accurate. When n < 30, the distribution cannot be considered normal. That is why we must use t-statistics in this case. The t-table takes into account the non normal distribution of the small sample size.

### At What Temperature Should We Consider Someone's Temperature "Abnormal"?
In this EDA, everything has been based off of the 95% confidence interval. For this particular question, it is not unfeasible to use the 99% confidence interval. In other words, any temperature outside of the 99% confidence interval for the distribution of sample means would be consider abnormal. This interval as calculated is:
> **_98.089<sup>o</sup> - 98.414<sup>o</sup>_**

> Any temperature outside of this interval can be considered "Abnormal"

### Is There a Significant Difference in Temperature Between Male and Females
**********************
We saw in the initial data inspection that women's temperatures seemed to be on average 0.3<sup>o</sup> higher than that of males. If we consider the two samples of 65 males and 65 females as independent samples, we can perform a two sample t-test to see if there truly is a significant difference in average temperatures between males and females, or if this 0.3<sup>o</sup> difference was a one-off fluke, only to be seen in this particular sampling. A two sample t-test in essence is performed the same way a one sample test is performed (as we did above). The only difference between the two test is that instead of using the sample mean x&#772; as the statistic of interest, we use the difference in sample means x&#772; = x&#772;<sub>2</sub> - x&#772;<sub>1</sub>. And the standard deviation (in this case known as the standard error) is &theta; = s<sub>1</sub> + s<sub>1</sub> = <img src="https://latex.codecogs.com/svg.latex?\inline&space;\sqrt{\frac{{\theta_{1}}^{2}}{n_{1}}&space;&plus;&space;\frac{{\theta_{2}}^{2}}{n_{2}}&space;}" title="\sqrt{\frac{{\theta_{1}}^{2}}{n_{1}} + \frac{{\theta_{2}}^{2}}{n_{2}} }" />. Where these equations come from are out of the scope of this EDA. However the reader can see more information [here](http://onlinestatbook.com/2/sampling_distributions/samplingdist_diff_means.html). The process is the same now as the one sample t-test.
> H<sub>0</sub>: The mean difference in average temperature between male and female is 0 (meaning males and females have the exact same average temp)

Process
********
* Sample the normal distribution using mean x&#772; = 0 and standard deviation &theta; = s<sub>1</sub> + s<sub>2</sub> = <img src="https://latex.codecogs.com/svg.latex?\inline&space;\sqrt{\frac{{\theta_{1}}^{2}}{n_{1}}&space;&plus;&space;\frac{{\theta_{2}}^{2}}{n_{2}}&space;}" title="\sqrt{\frac{{\theta_{1}}^{2}}{n_{1}} + \frac{{\theta_{2}}^{2}}{n_{2}} }" />
* Calculate the 95% confidence interval for this distribution of means
* If our two sample mean difference is outside of this interval then reject the null hypothesis

The 95% confidence interval and interpretation for this distribution is:

> **With a calculated 95% confidence interval of -0.245 to  0.248, the sample mean difference of 0.3<sup>o</sup> is outside of this interval. The probablity of getting this mean difference was p-value = 0.024 or 2.4% which is below the 5% critical threshold. This means that there is a significant difference in average temperatures between males and females. Females on average do have a higher average temperature than males**

<p align="center">
  <img src="https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/EDA_human_temperature/images/difference.JPG">
</p>

<p align="center">
  <img src="https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/EDA_human_temperature/images/twosample.JPG">
</p>

# Conclusion
**************
Given the sample of 130 body temperatues and using Bootstrap Statistics in conjunction with Frequentist Statistics, it has been inferred that the historically accepted average temperature of 98.6<sup>o</sup> is incorrect. In fact, it can be stated that with 95% confidence that the population's average temperature is in the range of
> # **_98.089<sup>o</sup> - 98.414<sup>o</sup>_**

It has also been show, that on average, women have a higher average body temperature than that of their male counterparts. With 95% confidence, this difference in temperature can be in the range of
> # **_0.05<sup>o</sup> -  0.55<sup>o</sup>_**







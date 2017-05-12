# Propsper Loan Data Analysis
-- Details can be find at https://shawnxiaolongyang.github.io/LoanData_Exploration_by_Xiaolong.html

Prosper is America¡¯s first peer-to-peer lending marketplace, with more than 2 million members and over $2,000,000,000 in funded loans.

The Prosper loan dataset contains 81 variables, with almost 114000 observations. However, not all of the variables are valuable to explore. To get enough information of both loans and borrowers, I would focus on variables for loans, such as loan amount, loan original date, estimated return of loan, current loan status, and variables for borrowers, such as borrowers Prosper rating, Prosper score, listing category,borrower APR, borrower income, borrower employment status, borrower occupation, borrower home owner, borrower credit history, borrower state, borrower total Prosper loans. 

# Univariate Analysis
#### What is the structure of your dataset?
The data contains 113,937 rows and 81 different variables. The type of data I analyzed is int, num and factor.

#### What is/are the main feature(s) of interest in your dataset?
The loan original amount and the borrwoerAPR are the main features of my interest. The formor decided how much money borrowers want and capable to borrow, the latter decided how much interests rate did borrowers need to pay for the debt. The Prosper would like the most amount of loan for borrowers who can pay back, and borrowers want to have the least APR to rent the same amount of debt.

#### What other features in the dataset do you think will help support your investigation into your feature(s) of interest?
I thought all the variables I picked would be helpful to find how Prosper decided their original loan amount and at which APR borrowers would like to debt.

#### Did you create any new variables from existing variables in the dataset?
Yes. The loan original date provided were precise to day, to make it easier to find the trend, I reallocated the data by year. The data of ListingCategory provided only the identigy number, I renamed then the by Variable Definitions file. The employment Status Duration were allocated by month, I reallocated it by year. I also transferred the abbreviation of state to the full name.

#### Of the features you investigated, were there any unusual distributions? Did you perform any operations on the data to tidy, adjust, or change the form of the data? If so, why did you do this?
The histogram of loan original year showed a big dip among 2009. It is reasonal since there was the gloabl financial crisis. Most of the factor data I have reorder their levels for pretty plot. Most of number data I have cleaned the outliers to show the main part.

# Bivariate Analysis
#### Talk about some of the relationships you observed in this part of the investigation. How did the feature(s) of interest vary with other features in the dataset?
When loan original amount increased, the monthly loan payment would increase, borrowerAPR would also increase. When loan original amount was lower, there would be more bad debt, lower prosper rating, and more pre-2009 debt. When borrowerAPR increased, the estimated return would increase, the prosper score would decrease, and the credit score would decrease. When the borrowerAPR is close the 0.25, there would be more debt in process, more post-2009 debt.

#### Did you observe any interesting relationships between the other features (not the main feature(s) of interest)?
The state map with average income and percentage of homeowners of borrowers was the most interesting. If the state is on the coast, its borrowers would have higher average income but lower percentage of homeowners. If the state if far away from sea, its borrowers would have lower average income but higher percentage of homeowners.

#### What was the strongest relationship you found?
The relationship between monthly payment and original total amount, its corelation is 0.93.

# Multivariate Analysis
#### Talk about some of the relationships you observed in this part of the investigation. Were there features that strengthened each other in terms of looking at your feature(s) of interest?
Loan status and Prosper rating differentiated the relationship between monthly payment and loan original amount and the relationship between credit score and borrower APR. Loan status and prosper rating strendthened each other at borrowerAPR from the last graph, since higher borrowerAPR indicated less likedly to pay back, where bad debt percentage is higher; For those who were more likely to have a bad debt, they would more likely to have a lower prosper rating.

#### Were there any interesting or surprising interactions between features?
The most interesting interaction is the propsperrating with borrowerAPR and credit score, we can find there are different layers for different prosper raing. The most surprising interaction is the loan original year with loan original amount and monthly payment. It seems a common sense that there should be a different between post-2009 and pre-2009, however, there were not such a big difference.

#### OPTIONAL: Did you create any models with your dataset? Discuss the strengths and limitations of your model.
I have create general linear model to help me whether some of the factors could classify the data, and it shows that is true. The strength of model is that it can be calculated and proved, the weakness is that it is not straight forward as graph.

# Reflection
The Prosper loand dataset contains 81 variables for over 110,000 lines data. I started from two sides, one descibe the information about loan, another about borrowers, and picked 20 variables. I explord their distribution and find those interesting question and lead to the core of the each sides: Loan origianl amount and Borrowers APR. I used correation and covariance to analyze the relationship between other variables and the core in Bivariate analysis section. Eventually, I use AIC to find whether add another variables would make the sense in multivariate analysis.

During the process, I used library dplyr to clean, subset, group and summerize data, ggplot to plot data, map to plot state map or GIS information, corrplot to show the correlation coefficient, colorbrewer to show the gradient difference between different levels of data.

There was a clear trend between the loan original amount and monthly loan payment, estimated return, prosper rating, loan original year and occupation. There was another trend between the BorrowerAPR and Prosper rating, borrowers credit range, loan status, loan original year and occupation. I struggled understanding the relationship among loan original amount, monthly loan payment and loan status, and search for the financial definition to generate a new variable called Duration, which help us easily distinguish who might have bad debt.

Till now, the analysis focus more on data exploration without building a predict or classify model. For further analysis, I can use general linear model to combine both numeric and factors variables for prediction and classification. Prosper can benefit from the model to find who might have more bad debt, how much should they set the origianl amount for different borrowers and how much would they earned from them.

# Reference
How to order the (factor) variables in ggplot2 https://kohske.wordpress.com/2010/12/29/faq-how-to-order-the-factor-variables-in-ggplot2/

Prosper Loan Data - Variable Definitions https://docs.google.com/spreadsheets/d/1gDyi_L4UvIrLTEC6Wri5nbaMmkGmLQBk-Yx3z0XDEtI/edit#gid=0

US State Maps using map_data() https://www.r-bloggers.com/us-state-maps-using-map_data/

Split time series data http://stackoverflow.com/questions/13649019/with-r-split-time-series-data-into-time-intervals-say-an-hour-and-then-plot-t

Use corcolor to plot correlation http://www.sthda.com/english/wiki/correlation-matrix-a-quick-start-guide-to-analyze-format-and-visualize-a-correlation-matrix-using-r-software

colors in R http://www.stat.columbia.edu/~tzheng/files/Rcolor.pdf

# Reproducibility
## R version 3.3.1 (2016-06-21)
## Platform: x86_64-w64-mingw32/x64 (64-bit)
## Running under: Windows 10 x64 (build 14393)
## 
## locale:
## [1] LC_COLLATE=English_United States.1252 
## [2] LC_CTYPE=English_United States.1252   
## [3] LC_MONETARY=English_United States.1252
## [4] LC_NUMERIC=C                          
## [5] LC_TIME=English_United States.1252    
## 
## attached base packages:
## [1] stats     graphics  grDevices utils     datasets  methods   base     
## 
## other attached packages:
## [1] scales_0.4.1       RColorBrewer_1.1-2 corrplot_0.77     
## [4] GGally_1.3.0       dplyr_0.5.0        maps_3.1.1        
## [7] ggplot2_2.2.0     
## 
## loaded via a namespace (and not attached):
##  [1] Rcpp_0.12.6         plyr_1.8.4          tools_3.3.1        
##  [4] rpart_4.1-10        digest_0.6.10       base64_2.0         
##  [7] htmlTable_1.7       evaluate_0.10       tibble_1.2         
## [10] gtable_0.2.0        lattice_0.20-34     Matrix_1.2-6       
## [13] DBI_0.5-1           yaml_2.1.14         gridExtra_2.2.1    
## [16] cluster_2.0.4       stringr_1.0.0       knitr_1.15.1       
## [19] nnet_7.3-12         rprojroot_1.1       grid_3.3.1         
## [22] data.table_1.10.0   reshape_0.8.6       R6_2.2.0           
## [25] survival_2.40-1     foreign_0.8-66      rmarkdown_1.3      
## [28] latticeExtra_0.6-28 Formula_1.2-1       magrittr_1.5       
## [31] backports_1.0.4     Hmisc_4.0-1         htmltools_0.3.5    
## [34] splines_3.3.1       assertthat_0.1      colorspace_1.2-6   
## [37] labeling_0.3        stringi_1.1.1       acepack_1.4.1      
## [40] lazyeval_0.2.0      openssl_0.9.5       munsell_0.4.3
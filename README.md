# Investigating the Relationship Between Music Habits and Music Type with Mental Health States

## Introduction
Music has been an integral part of human culture throughout history and its significance has only intensified with the advancement of digital technology. The International Federation of the Phonographic Industry (IFPI) reported that the average weekly time listening to music grew from 18.4 hours in 2021 to 20.7 hours in 2023, the maximum time spent ever before [1]. Simultaneously, music plays an important role in supporting mental health, with 71% of interviewees declaring that it contributes positively to their well-being. For example, Panteleeva et al. demonstrated that music helps to reduce anxiety in nonclinical patients [2], which is extremely common worldwide, affecting 18% of the US population [3, 4]. Additionally, music's effects on OCD have shown therapeutic potential, although its significance remains to be proven [5].

An examination of the literature reveals that most research only employs one type of music and concentrates on the music intervention, not examining the correlation of various genres. Also, some studies on the chosen dataset have focused on the demographics of the respondents. Although they did some research on the relationship between music listening habits and type of music with mental health, the correlation between musical preferences, music listening habits, and mental health status has not been thoroughly explored. Thus, this study aims to understand music's therapeutic potential by investigating two primary hypotheses:

1. Individuals' music listening habits, including the duration and context of listening to music (e.g. while working), along with their background in composing or playing musical instruments influence their mental health and how they perceive music's benefits to their well-being.
2. Individuals' preferences for a type of music, including their favourite genre and foreign music, might also impact their mental health state and perceptions of music's effectiveness in supporting their mental health.

## Methodology
**Data.** The dataset used in this study was sourced from Kaggle [6], an online platform for data science competitions, datasets, and collaborative projects. Data was collected via a Google form without any restrictions on age or location, resulting in 736 observations. The survey gathered background information such as age and listening habits (e.g. number of hours per day, streaming platform, listening while working). Respondents also ranked their frequency of listening to 16 music genres and their mental health on a scale from 0 (not concerned) to 10 (frequent symptoms) for anxiety, OCD, insomnia, and depression, as well as how music affects their mental health (improve, no effect, worsen).

This dataset has a total of 33 variables that include both quantitative variables such as age, hours per day, and mental health metrics (anxiety, depression, insomnia, OCD) and categorical variables including primary streaming service, favourite genre, and various binary indicators (e.g. while working, instrumentalist, composer, exploratory). Additionally, it covers the frequency of listening to different music genres and the perceived effects of music on mental health. 

We decided to define new variables for each mental health disorder severity and music background. For mental health issues severity, we divided the rate from 0 to 10 into four categories: none (0), mild (1 to 3), moderate (4 to 6), and severe (7 to 10). This way we could not only simplify the analysis but get an improved interpretability of the results, as binning the frequency data helps in highlighting trends and patterns that might be obscured in the dataset. Additionally, we also combined the 'composer' and 'instrumentalist' variables into a derived variable called 'background' which contained categories consisting of none, composer, instrumentalist, and both. This new variable encompasses the information that is provided by both of the variables and provides valuable insights from the data, contributing to a more comprehensive understanding of the survey results.

Another crucial step was encoding categorical variables. Survey questions with categorical responses were transformed into numerical values. This transformation is essential for many statistical analyses that require numerical input. Encoding categorical variables ensures that the data can be effectively utilized by these techniques, thereby enhancing the robustness and accuracy of the analytical models. These preprocessing steps were crucial in preparing the dataset for subsequent analysis, ensuring that the data was clean, consistent, and appropriately formatted before the analysis.

### Hypothesis 1
This hypothesis focuses on the relationship between music habits, including the number of hours participants listen to music and whether they listen to music while working, and their musical background with mental health and the perceived effectiveness of music.

To analyze the relationship between music habits and mental health, we categorized daily music listening hours into bins ('0-2', '2-4', '4-6', '6-8', '8-10', '10-12', '12+'). Descriptive statistics (medians and IQRs) for OCD, depression, and insomnia scores were calculated. Correlation and linear regression analyses explored these relationships. The perceived effect of music on mental health was assessed using an ordered logistic regression model, with ANOVA and Kruskal-Wallis tests comparing listening duration across perceived effect groups.

For the "while working" variable, bar charts and boxplots identified trends in mental health severity. T-tests and Mann-Whitney tests further investigated these relationships. Crosstab analysis and chi-square tests determined the association between listening while working and perceived effects, with adjusted standardized residuals highlighting specific differences.

To examine the relationship between musical background and mental health variables (OCD, depression, insomnia, anxiety), ANOVA tests were performed followed by Tukey's HSD tests. Crosstab analysis and chi-square tests assessed the relationship between musical background and perceived effects of music, with heatmaps visualizing the results.

### Hypothesis 2
We want to explore individuals' preferences for a type of music, including their favourite genre and foreign music, which might also impact their mental health state and perceptions of music's effectiveness in supporting their mental health.

To investigate the relationship between favourite genres and mental health variables (OCD, depression, insomnia, anxiety), we used crosstab analysis and bar charts to visualize the severity distribution across genres. ANOVA tests were conducted for each mental health measure, followed by Tukey's HSD tests for significant results to identify specific group differences.

The relationship between favourite genres and perceived music effects was examined using chi-square tests for each genre. Contingency tables analyzed the association between music frequency for each genre and perceived music effects. The chi-square results, including statistics, p-values, and degrees of freedom, were compiled into a summary table for visualization.

To examine the relationship between exploration and mental health variables, crosstab analysis and bar charts visualized the distribution of exploratory behavior across severity levels. Normality and homogeneity of variances were tested, and effect sizes (Cohen's d) were calculated. Kruskal-Wallis tests compared mental health variables across exploratory groups, with eta squared used for effect size. Mann-Whitney U tests and rank-biserial effect sizes were also calculated.

Crosstab analysis and bar charts were used to explore the relationship between knowing foreign languages and mental health variables. Normality and homogeneity of variances were assessed, and effect sizes (Cohen's d) were calculated. Kruskal-Wallis tests and Mann-Whitney U tests along with their effect sizes were performed.

Finally, to investigate the relationship between knowing foreign languages and perceived music effects, crosstab analysis and count plots were utilized. A chi-square test of independence determined the significance of the association, with results including chi-square statistics, p-values, degrees of freedom, and expected frequencies.

## Results
### Hypothesis 1: Impact of Music Habits and Background on Mental Health and the Perceived Effectiveness of Music Therapy
**Hours per Day <> Mental Health and Music effect.** There is a weak positive correlation between the hours per day of listening to music and the severity of mental health conditions (OCD, depression, insomnia, and anxiety). This implies that as the number of listening hours increases, the severity of these conditions slightly increases.

![Median Mental Health Scores by Daily Music Listening Duration](path_to_figure1.png)

The relationship between the number of hours participants listen to music per day and various mental health severity levels was examined using OLS regression models. The table below summarizes the result of the regression model.

| Dependent Variable | Coefficient (Hours per Day) | Standard Error | t-value | p-value | R-squared | Adjusted R-squared |
|--------------------|----------------------------|----------------|---------|---------|-----------|---------------------|
| Depression Severity| 0.0199                     | 0.013          | 1.507   | 0.132   | 0.004     | 0.002               |
| Insomnia Severity  | 0.0339                     | 0.014          | 2.411   | 0.0162  | 0.009     | 0.008               |
| Anxiety Severity   | 0.0095                     | 0.012          | 0.801   | 0.424   | 0.001     | -0.001              |
| OCD Severity       | 0.0322                     | 0.013          | 2.413   | 0.0161  | 0.009     | 0.008               |

The OLS regression analysis revealed significant relationships between daily music listening hours and the severity of OCD and insomnia. For OCD severity, the coefficient was 0.0322 (p = 0.0161) and for insomnia severity, the coefficient was 0.0339 (p = 0.0162) indicating that increased music listening hours are associated with higher severity levels of OCD and insomnia. No significant relationships were found for depression (p = 0.132) or anxiety (p = 0.424).

![Histogram of Hours per Day by Perceived Music Effects](path_to_figure2.png)

The data suggests that listening to music (hours per day) is generally perceived as either improving the experience or having no effect, with very few instances of worsening the experience. (Figure 2) As the duration increases, the frequency of perceived improvement remains high, while instances of no effect or worsening are relatively rare.

Both ANOVA (stat = 0.65, p = 0.52) and Kruskal-Wallis tests (stat = 4.67, p = 0.097) indicate no strong evidence of significant differences in the duration of music listening per day across different categories of music effects. The Kruskal-Wallis p-value is close to 0.10, suggesting weak evidence of a difference that may require further investigation with a larger sample size.

**Listening to Music While Working <> Mental Health and Music effect.** Statistical tests indicate that listening to music while working is associated with higher OCD scores, evidenced by significant results from both the t-test and the Mann-Whitney U test. However, no significant differences in depression, insomnia, or anxiety scores were found.

| Variable          | Test                 | Statistic | p-value  |
|-------------------|----------------------|-----------|----------|
| OCD Severity      | t-test               | 2.81      | 0.0051   |
| OCD Severity      | Mann-Whitney U test  | 35649.0   | 0.0050   |
| Depression Severity| t-test               | 1.28      | 0.2005   |
| Depression Severity| Mann-Whitney U test  | 32987.0   | 0.2141   |
| Insomnia Severity | t-test               | 0.86      | 0.3902   |
| Insomnia Severity | Mann-Whitney U test  | 32276.0   | 0.4142   |
| Anxiety Severity  | t-test               | 0.98      | 0.3299   |
| Anxiety Severity  | Mann-Whitney U test  | 37715.0   | 0.7941   |
Music_Mental_Health/images

![Effect of listening to music while working on mental health](./Music_Mental_Health/images/figure1.JPG)


The relationship between listening to music while working and the perceived effects of music was examined using a chi-square test of independence. The analysis revealed a statistically significant relationship between these variables (Chi-square statistic = 14.05, p = 0.0009, degrees of freedom = 2).

![The effect of music for those who listen while working](path_to_figure4.png)

The adjusted standardized residuals with p-values in the heatmap highlight that individuals who listen to music while working are more likely to report an improvement in their state. Conversely, those who do not listen to music while working are more likely to report no effect or an improvement, with very few reporting a worsening effect. This suggests that the context of working significantly influences the perceived effects of music.

**Background (composer instrumental) <> Mental Health and Music effect.**

![Levels of each mental health condition for each musical background](path_to_figure5.png)

The relationship between musical background (composer, instrumental) and mental health variables (OCD, depression, insomnia, anxiety) was examined using ANOVA and Tukey's HSD tests. The ANOVA results showed no significant differences in the severity of OCD (F = 1.10, p = 0.35), depression (F = 1.69, p = 0.17), insomnia (F = 1.76, p = 0.15), or anxiety (F = 0.77, p = 0.51) across different musical backgrounds. Tukey's HSD tests confirmed that there were no significant pairwise differences between any of the groups for these mental health variables. The box plot illustrates the distribution of mental health scores for different musical backgrounds, further supporting the finding that musical background does not significantly influence the severity of these mental health conditions.

![The relationship between the musical background and the effect of music on mental health](path_to_figure6.png)

The chi-square test revealed a weak association between musical background and perceived music effects (Chi-square statistic = 11.41, p = 0.076). The heatmap of adjusted standardized residuals indicates that individuals with no musical background ("None") are significantly more likely to report "No effect" from music, driving the observed association.

### Hypothesis 2: Music Preferences and Mental Health
**Favorite genre <> Mental Health and Music effect**

![Severity count per favorite music genre](path_to_figure7.png)

The bar charts in Figure 7 illustrate the severity count of various mental health conditions (anxiety, depression, insomnia, and OCD) across different favorite music genres. The data shows that Metal, Rock, and Pop genres have higher counts of severe levels for these conditions. Particularly, anxiety and depression show a higher proportion of severe cases among individuals who prefer these genres. The ANOVA results indicate a significant effect of genre on depression (F = 1.84, p = 0.027) and insomnia (F = 1.95, p = 0.017) but not on OCD (F = 0.44, p = 0.968) or anxiety (F = 1.10, p = 0.348). Tukey's HSD post hoc test found no significant pairwise differences between specific genres for depression and insomnia, suggesting that while there is a general effect of genre, individual differences between genres are not significant. Overall, the data suggests that Metal, Rock, and Pop are associated with higher severity of mental health conditions, particularly anxiety and depression.

![Music effect count per favorite music genre](path_to_figure8.png)

The bar charts in Figure 8 illustrate the perceived effects of music (improve, worsen, no effect) across different favourite music genres for various mental health conditions (anxiety, depression, insomnia, OCD). The Chi-square test results show no significant association between favourite genre and perceived music effects (Chi2 statistic = 37.35, p = 0.167, degrees of freedom = 30). This suggests that the variations observed in the bar charts do not indicate a statistically significant pattern. The expected frequencies for each genre and effect category further support that the perceived effects of music are not significantly influenced by the favorite music genre.

**Frequency of listening to each genre <> Mental Health and Music effect**

![Correlated music genre with mental health disorders](path_to_figure9.png)

The heatmap in Figure 9 shows the correlation between the music genre and mental health variables such as OCD, Depression, Insomnia, and Anxiety. Frequent listening to EDM is associated with higher levels of OCD, depression, and insomnia. Specifically, the correlation with OCD severity is 0.1 (p-value of 0.013), with depression severity is 0.08 (p-value of 0.046), and with insomnia severity is 0.104 (p-value of 0.01). This suggests that individuals who listen to EDM more often tend to report more severe symptoms of these mental health conditions. The frequency of listening to Metal music shows a strong positive correlation with both depression and insomnia severity. The correlation with depression severity is 0.141 (p-value of 0.000) and insomnia severity is 0.13 (p-value of 0.001). This indicates that frequent Metal listeners tend to experience more severe symptoms of depression and insomnia. Rock music is correlated with increased severity of depression and insomnia. The correlation with depression severity is 0.179 (p-value of 0.000) and insomnia severity is 0.08 (p-value of 0.046). This implies that more frequent listening to Rock music is associated with higher levels of these conditions. There is a positive correlation between listening to Lofi's music and insomnia severity. The correlation is 0.1 (p-value of 0.013), suggesting that frequent Lofi listeners are more likely to experience more severe insomnia symptoms. Frequent listening to Video Game Music is associated with higher levels of insomnia and anxiety. The correlation with insomnia severity is 0.095 (p-value of 0.018) and with anxiety severity is 0.106 (p-value of 0.009). This suggests that individuals who listen to Video Game Music more often tend to report more severe symptoms of insomnia and anxiety.

In summation, certain genres of music, namely EDM, Metal, Rock, Lofi, and Video Game Music, have positive correlations with various mental health conditions. Frequent listening to these genres is associated with higher severity of OCD, depression, insomnia, and anxiety, indicating a potential impact of music preferences on mental health. Although the correlation coefficients are not too high, we believe that when more data is collected, we will see more meaningful results for the various relationships.

The chi-square test results indicate no significant association between the frequency of listening to various music genres and the perceived effects of music on mental health. For example, classical music had a chi-square statistic of 2.06 (p = 0.91), country music had a chi-square statistic of 5.95 (p = 0.43), and EDM had a chi-square statistic of 8.66 (p = 0.19). Similarly, genres such as hip hop (chi-square = 7.26, p = 0.30), jazz (chi-square = 2.77, p = 0.84), and metal (chi-square = 2.24, p = 0.90) also showed no significant association. The highest chi-square statistic was observed for R&B (chi-square = 11.18, p = 0.08), but it still did not reach statistical significance. Overall, the p-values for all tested genres were greater than 0.05, indicating that the perceived effects of music are not significantly influenced by the favorite music genre.

**Exploration <> Mental Health and Music Effect**

![The distribution of relationship between the exploratory behavior and the mental health disorders](path_to_figure10.png)

The relationship between exploratory behaviour and mental health variables (OCD, depression, insomnia, anxiety) was analyzed using several statistical tests. The normality tests for OCD (W = 0.848, p < 0.001), depression (W = 0.946, p < 0.001), insomnia (W = 0.915, p < 0.001), and anxiety (W = 0.946, p < 0.001) all indicated non-normal distributions. Homogeneity of variances tests for these variables showed no significant differences in variances.

Cohen's d values were small for OCD (0.08), depression (0.13), insomnia (0.11), and anxiety (0.05) suggesting minimal effect sizes. Kruskal-Wallis tests showed no significant differences in mental health variables across exploratory groups: OCD (H = 0.72, p = 0.3946), depression (H = 2.11, p = 0.1462), insomnia (H = 2.13, p = 0.1444), and anxiety (H = 0.07, p = 0.7939). Effect sizes (eta squared) for these tests were near zero.

Mann-Whitney U tests also showed no significant differences: OCD (U = 38836.00, p = 0.3948), depression (U = 40035.00, p = 0.1463), insomnia (U = 40041.00, p = 0.1445), and anxiety (U = 37715.00, p = 0.7941). Rank-biserial effect sizes were small for OCD (-0.04), depression (-0.08), insomnia (-0.08), and anxiety (-0.01). Overall, these results suggest no significant relationship between exploratory behaviour and the severity of mental health conditions.

![The relationship of exploratory behavior and the perceived effects of music](path_to_figure11.png)

The relationship between exploratory behavior and the perceived effects of music was analyzed using a chi-square test. The chi-square statistic was 13.81 (p = 0.001), indicating a significant association between exploratory behavior and perceived music effects. The degrees of freedom for this test were 2.

**Listening to Foreign songs <> Mental Health and Music effect**

![The distribution of the relationship between knowledge of foreign languages and mental health disorders](path_to_figure12.png)

The relationship between knowledge of foreign languages and mental health variables (OCD, depression, insomnia, anxiety) was examined. Normality tests indicated non-normal distributions. Homogeneity of variances tests showed no significant differences for any mental health conditions.

The Kruskal-Wallis tests revealed significant differences for depression (H = 4.98, p = 0.0257) and anxiety (H = 4.22, p = 0.0399) but not for OCD or insomnia. Mann-Whitney U tests confirmed these findings: depression (U = 51534.00, p = 0.0257) and anxiety (U = 51143.00, p = 0.0399).

Cohen's d values suggested minimal effect sizes: OCD (-0.08), depression (0.17), insomnia (0.09), and anxiety (0.16). These results indicate a weak but significant relationship between knowledge of foreign languages and the severity of depression and anxiety, with no significant relationship between OCD and insomnia.

![The relationship between the knowledge of foreign languages and perceived music effects](path_to_figure13.png)

The relationship between knowledge of foreign languages and perceived effects of music was examined using a chi-square test. The results showed no significant association, with a chi-square statistic of 0.169 (p = 0.919) and 2 degrees of freedom. Expected frequencies for those who know foreign languages were 203.06 (Improve), 59.39 (No effect), and 6.55 (Worsen), while for those who do not know foreign languages, the expected frequencies were 261.94 (Improve), 76.61 (No effect), and 8.45 (Worsen). These findings suggest that knowledge of foreign languages does not significantly influence how individuals perceive the effects of music.

## Discussion
This study underscores the complex relationship between music listening habits, genre preferences, and mental health. While music has the potential to be a powerful therapeutic tool, its effects vary widely depending on individual and contextual factors.

### Interpretation of Findings
The findings illustrate nuanced interactions between music listening habits, musical preferences, and various mental health conditions. These results highlight the complex relationship between the type of music individuals prefer and their listening behaviors with their overall mental well-being. By examining patterns and preferences in music consumption, we can better understand how certain genres or listening practices may correlate with or influence various mental health outcomes.

**Listening Duration and Mental Health Severity:** A weak positive correlation was found between the duration of music listening and the severity of mental health issues. This suggests that excessive music listening could potentially exacerbate symptoms of OCD, depression, insomnia, and anxiety. This aligns with existing research indicating that excessive listening to certain genres may lead to dysfunctional rumination, which is strongly associated with depression [7].

**Music While Working:** Listening to music while working appears to increase OCD symptoms, though it does not significantly impact depression, insomnia, or anxiety. This finding indicates that the context in which music is listened to plays a critical role in its effects on mental health. It suggests that while music can be beneficial, its impact varies depending on situational factors.

**Genre Preferences and Mental Health:** The study reveals significant associations between music genre preferences and mental health states. Different genres appear to influence mental health conditions in varied ways:

- **OCD:** A weak positive correlation with EDM suggests that frequent listeners of this genre may experience higher OCD symptoms.
- **Depression:** Genres such as rock, metal, rap, hip hop, and folk are associated with higher depression scores, possibly due to their lyrical themes and emotional intensity [9].
- **Insomnia:** Genres like metal, video game music, classical, Lofi, and EDM are linked with higher insomnia scores, perhaps due to their stimulating or complex nature [10].
- **Anxiety:** Video game music and pop show significant associations with anxiety, indicating that these genres may have elements that exacerbate anxiety symptoms [7].

**Foreign Language Music:** Listening to music in foreign languages shows significant effects on depression and anxiety. This finding aligns with the theory that music with less predictable elements can lead to more surprising and emotionally impactful experiences [8].

**Exploratory Behavior and Music Perception:** The relationship between exploratory behaviour and the perceived effects of music was found to be significant. We believe this is because people who are more willing to explore tend to be more open-minded and receptive to advice and others' perspectives. This openness may make them more likely to find music helpful as they are ready to change and accept help.

This finding aligns with existing research. For instance, McCrae found that individuals high in openness to experience are more likely to report experiencing aesthetic chills while listening to music, indicating deeper emotional engagement [11]. Chamorro-Premuzic and Furnham showed that people with higher levels of openness are more likely to use music for emotional regulation and cognitive stimulation [12]. Additionally, Rentfrow and Gosling demonstrated that those high in openness tend to have a more diverse range of music preferences and appreciate complex and unconventional music [13]. These studies support the notion that individuals who are more exploratory and open-minded are more likely to perceive music as beneficial.

### Practical Implications
These findings have several practical implications for the use of music as a therapeutic tool:

1. **Customized Music Therapy:** Tailoring music therapy to individual preferences and listening contexts may enhance its efficacy. For instance, avoiding certain genres for individuals with specific mental health conditions could prevent the exacerbation of symptoms.
2. **Mindful Listening:** Encouraging mindful music listening practices, particularly in contexts such as work, can help manage the potential negative impacts on mental health.
3. **Educational Programs:** Developing educational programs that inform the public about the potential effects of different music genres on mental health could foster healthier music listening habits.

### Limitations and Ethical Considerations
**Data Source:** The dataset was sourced from Kaggle, and while publicly available for research purposes, it was not custom-collected for this study. This could introduce biases or limitations in the data's applicability. For example, most participants in this survey are under 30 years old, with a median age of 20. Many other factors can influence people’s mental health and how they find it useful. Future studies should focus on the interaction between different factors and external factors not considered in this dataset. Moreover, a larger dataset could result in clearer outcomes.

**Self-reported Measures:** The reliance on self-reported measures for mental health and music listening habits may introduce subjective biases and inaccuracies.

**Ethical Concerns:** Ethical considerations are paramount, especially given the sensitive nature of mental health data. The dataset includes explicit consent for the use of individual responses, but continuous vigilance is necessary to ensure ethical use and interpretation of the data.

## References
1. IFPI. (2023). Engaging with Music 2023. Retrieved from [IFPI](https://www.ifpi.org/wp-content/uploads/2023/12/IFPI-Engaging-With-Music-2023_full-report.pdf)
2. Panteleeva Y., Ceschi G., Glowinski D., Courvoisier D.S., Grandjean D. (2018). Music for anxiety? Meta-analysis of anxiety reduction in non-clinical samples. *Psychol Music*, 46 (4), 473-487.
3. Remes O., Brayne C., Van Der Linde R., Lafortune L. (2016). A systematic review of reviews on the prevalence of anxiety disorders in adult populations. *Brain and Behavior*, 6(7), e00497. [DOI](https://doi.org/10.1002/brb3.497)
4. Simpson H. B., Neria Y., Lewis-Fernandez R., Schneier F. (2010). *Anxiety disorders – theory, research, and clinical perspectives* (1st ed.). Cambridge University Press.
5. Truong T.P.A., Applewhite B., Heiderscheit A., Himmerich H. (2021). A Systematic Review of Scientific Studies and Case Reports on Music and Obsessive-Compulsive Disorder. *Int. J. Environ. Res. Public Health*, 18, 11799. [DOI](https://doi.org/10.3390/ijerph182211799)
6. Rasgaitis C. (2022). Music & Mental Health Survey Results retrieved from: [Kaggle](https://www.kaggle.com/datasets/catherinerasgaitis/mxmh-survey-results?resource=download)
7. Gebhardt S., Kunkel M., & von Georgi R. (2016). The role musical preferences play in the modulation of emotions for people with mental disorders. *The Arts in Psychotherapy*, 47, 66–71. [DOI](https://doi.org/10.1016/j.aip.2015.12.002)
8. Gebauer L., Kringelbach M. L., & Vuust P. (2012). Ever-changing cycles of musical pleasure: The role of dopamine and anticipation. *Psychomusicology*, 22(2), 152–167. [DOI](https://doi.org/10.1037/a0031126)
9. Gustavson D. E., Coleman P. L., Iversen J. R., Maes H. H., Gordon R. L., & Lense M. D. (2021). Mental health and music engagement: review, framework, and guidelines for future studies. *Translational Psychiatry*, 11(1). [DOI](https://doi.org/10.1038/s41398-021-01483-8)
10. Droit-Volet S., Ramos D., Bueno J. L. O., & Bigand E. (2013). Music, emotion, and time perception: the influence of subjective emotional valence and arousal? *Frontiers in Psychology*, 4. [DOI](https://doi.org/10.3389/fpsyg.2013.00417)
11. McCrae R. R. (2007). Aesthetic Chills as a Universal Marker of Openness to Experience. [DOI](https://psycnet.apa.org/doi/10.1007/s11031-007-9053-1)
12. Chamorro-Premuzic T., Furnham A. (2007). Personality and music: can traits explain how people use music in everyday life? *Br J Psychol.*, 98(Pt 2), 175-85. [DOI](https://doi.org/10.1348/000712606X111177)
13. Rentfrow P. J., & Gosling S. D. (2003). The do re mi's of everyday life: The structure and personality correlates of music preferences. *Journal of Personality and Social Psychology*, 84(6), 1236–1256. [DOI](https://doi.org/10.1037/0022-3514.84.6.1236)

## Code and Related Works
Code and related works provided on the Colab link: [here](https://drive.google.com/file/d/1hyfaBk7brJZAQbwOjDDg9AprdaObcnpm/view?usp=sharing)

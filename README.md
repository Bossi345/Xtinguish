# Xtinguish Open Source Project

## About the Project

### What are Forest Fires?

Forest fires, also known as wildfires, are uncontrolled and usually destructive fires. They occur in forests, grasslands, or other natural landscapes. These fires can vary in size and intensity, from small and manageable to large and devastating.

### Causes of Forest Fires

Forest fires have many causes, some occuring naturally while others are caused my human factors. Some natural factors include temperature abnormalities, decreased humidity, ecological variance, and lightning strikes. Some human factors include agricultural burning and discarding of flammable objects.

The main causes of forest fires are shifts in temperature and humidity. According to a study on spatial and temporal expansions of global wildfire activity due to climate change, there is greater influence of climate than of human activities.

### Impacts of Forest Fires

**Climate Change**

Forest fires release a large amount of carbon contained by forests. These carbon emissions lead to a thicker greenhouse gas layer, making climate change to become severe. This, in turn, leads to exagerated temperatures and arid environments, causing even more forest fires.

**Threat to Biodiversity**

The forest is home to a variety of animal species, which are keys to keeping the ecosystem in place. Within these complex ecosystems also lie endangered species. A single forest fire could be the final blow, leaving no legacy for future generations to see.

**Human Lives and Livelihood**

Communities living near fire-prone areas face immediate threats from fast-spreading wildfires. Many lives will be at risk when facing rapid forest fires. Moreover, many communities rely on the forest for resources or eco-tourism, thereby threatening their well-being and way of life.

**Air Quality and Public Health**

Smokes produced from forest fires deteriorate air quality, leading to a surge of respiratory, cardiovascular, and cancerous health issues. Even areas far from the fires can experience smoky conditions, affecting millions of people across countries. 

**Economic Impacts**

The cost of battling forest fires is enormous, draining the public's resources. Moreover, fires can destroy valuable natural resources such as timber. Forest fires reaching communities can dessimate crops, agricultural infrastructure, and homes, leading to vast economic losses. 

### Introduction to the Project

[<img src="https://img.youtube.com/vi/fejZKygYZek/hqdefault.jpg" width="320" height="220"
/>](https://www.youtube.com/embed/fejZKygYZek)

## Technical Framework

### Data Collection and Preprocessing

**Temperature Data:** Let $t_i$ be the temperature from sensor $i$ at a specific time. 
$T = [t_1, t_2, ..., t_n]$ where n is the number of sensors.

**Humidity Data:** Let $h_i$ be the humidity from sensor $i$ at a specific time.
$H = [h_1, h_2, ..., h_n]$ where n is the number of sensors.

### Feature Engineering

**Temperature Difference:**

For the sensed temperature and a baseline or expected temperature $t_{baseline}$, $\Delta T = T - t_{baseline}$. 

This will give a vector with temperature deviations from the baseline.

**Rolling Averages:**

For a rolling window size $w$, $RA_i = \frac{1}{w}\sum_{j=i-w+1}^{i}t_j$.

This provides smoothing and can capture trends.

### Multivariate Regression Model

Considering just temperature and humidity for simplicity: $F = \beta_0 + \beta_1T + \beta_2H + \epsilon$

Where:
- $F$ is the fire risk score.
- $\beta_0, \beta_1, \beta_2$ are coefficients.
- $\epsilon$ is the error term.

The aim is to fit this model using the training data and minimize the error.

### Anomaly Detection
Considering temperature as a feature, an anomaly score A for each data point can be computed using an algorithm like Isolation Forest.

### Notification System Integration

A simple rule-based thresholding can be applied:

If $F > F_{threshold}$ or $A > A_{threshold}$ then trigger alert

Where:
- $F_{threshold}$ is a threshold fire risk score.
- $A_{threshold}$ is a threshold anomaly score.

### Pipeline Construction for Fire Mitigation

If $F > F_{high}$, then activate sprinkler

Where:
- $F_{high}$ is a very high fire risk score, above which we deem it necessary to activate the sprinklers.

### Mathematical Considerations
1. Multicollinearity: When using multiple predictors, like temperature and humidity, they might be correlated. This can be checked using the Variance Inflation Factor (VIF). If VIF is too high for a predictor, consider removing it or using techniques like PCA.
2. Model Assumptions: Ensure the assumptions of regression are met — linearity, independence, homoscedasticity, and normality.
3. Outliers: The impact of outliers can be reduced using robust regression techniques or by preprocessing the data.
4. Model Evaluation: Use adjusted R-squared, AIC, BIC, and other metrics to determine the goodness of fit of the regression model. For anomaly detection, use metrics like precision, recall, and the F1-score to evaluate the performance on a held-out test set.
# Data Sheet

## Motivation

For what purpose was the dataset created?

- The author is not aware of the dataset being created for a specific purpose.

Who created the dataset (e.g., which team, research group) and on behalf of which entity (e.g., company, institution, organization)? Who funded the creation of the dataset?

- [Antoni Sobkowicz](https://zenodo.org/search?q=metadata.creators.person_or_org.name%3A%22Antoni%20Sobkowicz%22&l=list&p=1&s=10&sort=bestmatch), of the National Information Processing Institute, created the dataset for public user via [Zenodo](https://zenodo.org/records/1000885). It has also been made available via [Kaggle](https://www.kaggle.com/datasets/andrewmvd/steam-reviews). As far as the author is aware, the dataset was not funded by any entity.

## Composition

What do the instances that comprise the dataset represent (e.g., documents, photos, people, countries)?

- Each instances compromises a single review on the [Steam](https://store.steampowered.com/) storefront. They contain the application identifier and name of the game, the review text, the review's score (i.e., positive or negative), and the number of votes the review received. 

How many instances of each type are there?

- 6.4 million instances.
  
Is there any missing data?

- Some reviews are missing review text.

Does the dataset contain data that might be considered confidential (e.g., data that is protected by legal privilege or by doctor–patient confidentiality, data that includes the content of individuals’ non-public communications)?

- No, the dataset has been scrapped from publically available review data from the [Steam](https://store.steampowered.com/) storefront.

## Collection Process

How was the data acquired?

- The dataset was scrapped from the Steam storefront.

If the data is a sample of a larger subset, what was the sampling strategy? 

- The dataset is definitely part of a larger dataset compromising all reviews from the Steam storefront. The author is unsure of the sampling strategy.

Over what time frame was the data collected?

- The dataset seems to have been collected from 2017 and earlier.

## Preprocessing/Cleaning/Labelling

Was any preprocessing/cleaning/labeling of the data done (e.g., discretization or bucketing, tokenization, part-of-speech tagging, SIFT feature extraction, removal of instances, processing of missing values)? If so, please provide a description. If not, you may skip the remaining questions in this section.

- All instances with missing review text were removed, all text was changed to lowercase, multiple contiguous spaces were removed, and the negative labels were changed from -1 to 0. Finally the text was tokenised to be used in the convolutional neural network (CNN).

Was the “raw” data saved in addition to the preprocessed/cleaned/labeled data (e.g., to support unanticipated future uses)?

- Yes, all processing of the data was done on-demand in script.
 
## Uses

What other tasks could the dataset be used for?

- The dataset could potentially be used to judge the success or sales of the video games listed in it.

Is there anything about the composition of the dataset or the way it was collected and preprocessed/cleaned/labeled that might impact future uses? For example, is there anything that a dataset consumer might need to know to avoid uses that could result in unfair treatment of individuals or groups (e.g., stereotyping, quality of service issues) or other risks or harms (e.g., legal risks, financial harms)? If so, please provide a description. Is there anything a dataset consumer could do to mitigate these risks or harms? 

- The author is unaware of any concerns around the composition of the dataset.

Are there tasks for which the dataset should not be used? If so, please provide a description.

- None.

## Distribution

How has the dataset already been distributed?

- The dataset has been distributed via [Zenodo](https://zenodo.org/records/1000885). It has also been made available via [Kaggle](https://www.kaggle.com/datasets/andrewmvd/steam-reviews).

Is it subject to any copyright or other intellectual property (IP) license, and/or under applicable terms of use (ToU)?

- [Creative Commons Attribution Non Commercial 4.0 International](https://creativecommons.org/licenses/by-nc/4.0/legalcode)

## Maintenance

Who maintains the dataset?

- No maintenance seems to be ongoing at this time.

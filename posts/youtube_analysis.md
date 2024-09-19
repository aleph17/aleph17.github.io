---
layout: blog
---
## <span class="title-secondary"></span> Boost Your Tech Channel with A Numbers-Backed Analysis

> Since its launch in 2005, YouTube has grown into a massive platform for content creation, especially in the tech niche. But how can tech content creators stand out and thrive on YouTube in 2023? What are the best practices and strategies to attract and retain viewers and subscribers?
>

## <span class="section-bar"></span> Abstract

YouTube is a popular platform for content creation, especially in the tech niche. However, not all tech channels achieve the same level of success and popularity. What are the factors that influence the performance of a tech channel on YouTube? In this blog post, we will share the results of our in-depth analysis of a large collection of YouTube data. We will focus on the tech review channels and identify the key features that correlate with their success, such as video length, upload frequency, publishing date, and more. Based on our findings, we will provide some practical tips and recommendations for the tech YouTubers who want to improve their channel and grow their audience. 

## <span class="section-bar"></span> Dataset

To conduct our data analysis, we used the [YouNiverse](https://arxiv.org/abs/2012.10378) dataset, a comprehensive collection of YouTube data from various sources. The dataset includes metadata for over 136,000 channels and 72.9 million videos published between May 2005 and October 2019, as well as channel-level time-series data with weekly subscriber and view counts. The dataset was obtained from YouTube and two third-party websites that aggregate YouTube statistics: [channelcrawler.com](http://channelcrawler.com/) and [socialblade.com](http://socialblade.com/). 

Notice that the dataset includes the videos published between May 2005 and October 2019. We further narrowed the dataset focusing on the tech videos only for the sake of our analysis.

## <span class="section-bar"></span> Methods

Throughout our analysis, we used various methods to analyze the data from the YouNiverse dataset. We explored the general characteristics of successful tech review channels, such as the optimal video length, upload frequency, and the product types. We also examined how the sentiment of the video titles affects the viewership and engagement of the videos. Finally, we investigated the impact of big tech product releases on the channels' growth and the topics that are most relevant before and after the release. We used various metrics and techniques to measure and compare the performance and popularity of the tech channels, such as correlation, sentiment analysis, and topic modeling keeping in mind possible confounders of our analysis.

## <span class="section-bar"></span> Results

To wrap up our analysis of YouTube tech channels, we present the main results:

Optimal Video Length: Videos between 16 minutes and 2.7 hours are ideal to deliver valuable content and keep viewers interested. However, videos longer than 40 minutes are usually reserved for live events.

Upload Frequency: Regular and frequent video uploads with low variation lead to higher success and growth rates. Keeping up high regularity is vital for channels with 500k to 1M subscribers to sustain rapid growth.

Reviewed Product Type: The variety of reviewed product types does not affect channel growth significantly. Successful channels that cover a wide range of products tend to achieve the most success with videos on Phones, Desktop setups, Laptops, and Headphones.

Title Sentiment: Positive sentiments in video titles could be beneficial. Channels with positive language can increase views by up to a third compared to neutral titles. However, it is important to note that other factors, like thumbnails, could also affect the outcomes, which we did not have access to.

Product Release Events: Tech product releases, not only from big brands, offer a golden opportunity for channel growth. Talking about leaks and rumors before the launch creates excitement, and continuing coverage for a few months after the release is essential to attract the wider audience’s interest.

## <span class="section-bar"></span> Disclaimer

We remind the readers to not follow the guidelines blindly, but to experiment and innovate with their own content. Moreover, we acknowledge that the analysis may become outdated quickly, as YouTube is constantly changing and evolving. We do not claim to have complete or accurate information about YouTube or its content creators. The goal of this blog is to shortly present our insights from the analysis. The full data story can be read in [this](https://jakhongir0103.github.io/datastory/) link and the code can be found [here](https://github.com/epfl-ada/ada-2023-project-datasquad2023).

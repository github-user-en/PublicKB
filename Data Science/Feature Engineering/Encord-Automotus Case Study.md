# Problem
Automotus faced challenges with suboptimal model performance caused by poor data quality, including duplicates and corrupt images. Additionally, they found it difficult to prioritize the vast amounts of stored footage for labeling.

# Key Result
Leveraging Encord, they developed unified data pipelines with advanced visual data curation, including smart querying, filtering, and sorting, to focus on the most relevant data for labeling. This approach led to a 20% improvement in model performance, a 25% reduction in dataset size, and a 33% reduction in labeling cost.

# The Case Study
Upon evaluating other tools, the Automotus team partnered with Encord to manage their entire data pipeline for model development, from automated data curation to AI-assisted labeling to model evaluation. 

Here's a look at their entire workflow:

![[Pasted image 20240711124248.png]]

One of the team’s first priorities was converting the vast amount of de-identified images into labeled training data.

After first establishing a continuous annotation pipeline, the team faced a critical question: Among all the collected data, how could they ensure they were labeling the most relevant data? And, how would they identify such data?

The large volumes of de-identified images captured from hundreds of cameras presented an abundance of data. Labeling all of it would not necessarily improve model performance and would be prohibitively expensive.

Leveraging Encord, the team was able to **visually inspect, query, and sort their datasets** to eliminate undesirable low-quality data in just a few clicks.

This process resulted in a 35% reduction in the datasets' size for annotation. Consequently, the team achieved over a 33% reduction in their labeling costs.

The high model accuracy enabled Automotus to better serve and grow with their customers – presenting more accurate data to their clients: “From the modality distribution that happens at the street-level, to more accurate representations of the dwell times [and a few other metrics that we supply to our clients] – these base models are the ones driving these analytics.”

## How does Encord compare to other tools on the market?

The team evaluated several other tools on the market but ultimately decided to partner with Encord for several reasons: 

- **Flexible Ontology Structure**: Encord facilitated efficient object classification and tracking, allowing for straightforward ontology management and seamless training of both detection and classification models within a single project.
- **Quality Control Capabilities**: Encord's human-in-the-loop feedback mechanisms significantly enhanced annotation performance, particularly in identifying small objects within frames.
- **Automated Labeling Features**: The ability to label a few frames and use assisted labeling to speed up the process, reducing the need for manual labeling of every frame, was highly advantageous.

The Automotus AI team notes: “For example, a shortcoming with other tools was the quality of the labels: we’d occasionally realize bounding boxes would be tighter or too wide around the objects they were identifying, or objects wouldn’t be classified correctly within frames. Now, we can select the sampling rate of frames that we want to move towards a review process, and share real-time context with annotators so that they can also power our model performance. This human-in-the-loop approach means we can use Encord to help our annotators perform annotations better, which in turn speeds up how quickly we can improve our model performance. We are able to localize objects better and increase accuracy.”
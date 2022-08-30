# A brief context

------------------------------------------------------------------------

This was a pet project I developed in a post-graduate degree.

At the time we were asked to develop a full study on a dataset of our choosing, with the following checklist:

1.  Conceptualize a full DW for you data,
2.  Perform the entire ETL process,
3.  Generate a business semantic model from your DW,
4.  Create analytics dashboards from your semantic model,
5.  Apply a simple machine learning model into your data so you can makesome predictions

This project came in `step 2.`, where I decided to download my dataset from Kaggle into a given ADLS account using Databricks.

# About the notebook

------------------------------------------------------------------------

This notebook was developed in `Shell` and `Python/Pyspark`, and is sectioned in several `markdown` cells that introduce the main idea for the following code.

-   `Shell` is used to download the dataset from Kaggle and to use and organize the filesystem.
-   `Python/Pyspark` code is responsible for the widgets, mount and files' copy into the data lake (ADLS).

A simple UI was created using text widgets, so a user friendlier approach, with no in depth knowledge of the code, could be taken. For this, the first coded cell **(`cell 3`) needs to be ran, separately, first**.

This cell will create the widget UI like displayed bellow:

![](imgs/widget-layout.png){.illustration}

-   `Kaggle username`: insert your Kaggle account username.
-   `Kaggle key`: Refers to the Kaggle API token, created on your Kaggle account[^readme-1].
-   `Dataset url`: Copy the browsers' url from your selected dataset's page (the notebook will take care of the rest 😉).
-   `Working directory`: Chose a name for the folder you want to have your data stored in (in both cluster's driver[^readme-2] and ADLS).

[^readme-1]: Get complete information about this key and how to get [here](https://github.com/Kaggle/Kaggle-api#api-credentials).

[^readme-2]: Since I am using the community edition there is no problem with keeping a folder with the data on the driver (it's all temporary anyways), however, if you want to delete this folder and all data, from the cluster's driver, you can just add a new cell at the end and paste this code line: `%sh rm /Databricks/driver/$ddir/ -rf`

Finally, `cell 18` will need to be changed for each user. This cell is responsible for setting the mount point that connects Databricks to the ADLS service and the code wrapped in `<>` will need to be adjusted for each person/project.[^readme-3]

[^readme-3]: This connection was developed for a `Gen 2` storage account and more information about this setup/code-block can be found [here](https://docs.databricks.com/data/data-sources/azure/azure-storage.html).

![](imgs/ADLS-mount-cell.png){.illustration}

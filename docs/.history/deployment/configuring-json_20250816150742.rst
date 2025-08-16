Configuring Json File
=====================

An example Json file has been provided in the git repository for user's convenience, which looks like this:

.. figure:: ../assets/ConfigJson.png
   :width: 750
   
This config file can be edited the following way:

1. The user will be able to set the title of their Study in the "Study Name" place, depending on their dataset. [This field is mandatory and must be present, as the Nav-bar tabs is dependent on this field]
2. The "sc_data" row must contain the exact name of the AnnData or MuuData dataset that is to be used, and this dataset must be saved in any folder. [This field is mandatory if the user wants to visualize the Gene Expression]
3. The "description" row can be used to write the description of the study, and this is an optional field, although it is recommended to be added.
4. The "markers" row contains the important marker genes of the study. This field is important for visualization of the heatmap, dot plot, violin plot, stacked bar and pseudo time plot. However, it is not a required field and if the markers are not mentioned, the dropdown will show the top 6 genes, and the user can search for the relevant genes if needed.
5. The bucket_urls contains the link to the BigWig file for the ATAC seq (chromatin peaks in the IGV browser), it is advised to upload the data in an s3 bucket, as it is easier to call and doesn't have restrictive size requirement. However, this is not compulsory in general, and the user can keep this field empty if there is no BigWig file for their data.

   **Note:** The user can also follow the instructions provided in this link https://atacchloe.s3.eu-north-1.amazonaws.com.
6. The name for the ATAC track, the genome name for the ATAC sequences, and the max height of the browser can also be set. However, if the user has the BigWig file, these are important to mention as well as the bucket_urls.
7. Several ATAC seq tracks can be added as well, just follow the below given format:

   .. code-block:: json

      "bucket_urls": ["https://atacchloe.s3.eu-north-1.amazonaws.com/abc", "https://atacchloe.s3.eu-north-1.amazonaws.com/xyz", .......],
      "ATAC_name": ["Track1", "Track2", .......],
      "genome": "hg38",
      "max_height": [10, 20, ......]

8. If there is no ATAC-seq available for the provided dataset, user can simply remove the "bucket_urls", "ATAC_name", "genome" and "max_height" from the Json file.
9. Custom colors can also be set for the labels and clusters, following the hash code of the colors in the "color" section.
10. Several Datasets can be added the same way by the following way:

    .. code-block:: json

       {
          "Study1": {
          "sc_data": ---------
          },
       
          "Study2": {
          "sc_data": ---------
          },
       
          "color": [
           -------
          ]
       }

    and so on...
11. If the user only wants to visualize the BigWig, they do not need an input for the sc_data and markers

Once the config file is set, the AnnData file and the BigWig file are created, then GUANACO, with user's data can easily be accessed locally or deployed on any server. The information will be displayed in the marked places of the platform as shown in Figure 2.1, Figure 2.2, and Figure 2.3.

.. figure:: ../assets/Figure21.png
   :width: 600

xx

.. figure:: ../assets/Figure 2.2.png
   :width: 600

xx

.. figure:: ../assets/Figure 2.3.png
   :width: 600

xx

Once the json file is made, we are offering users two ways to deploy and access GUANACO; one version is running GUANACO from console using system's Python, and another one is with Docker.

|

.. raw:: html

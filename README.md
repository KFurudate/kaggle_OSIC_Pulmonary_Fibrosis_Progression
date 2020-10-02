# kaggle_OSIC_Pulmonary_Fibrosis_Progression
<img width="638" alt="Screen Shot 2020-09-29 at 13 14 52" src="https://user-images.githubusercontent.com/50528980/94599581-3edc4c80-0256-11eb-962c-cc5704b3d6c8.png">

https://www.kaggle.com/c/osic-pulmonary-fibrosis-progression
## 20200905
- The first step is to open the DICOM image.
          - reference: https://qiita.com/fukuit/items/ed163f9b566baf3a6c3f
     
- I learned the domain knowledge about idiopathic interstitial pneumonia.
          - reference: https://www.jrs.or.jp/quicklink/journal/nopass_pdf/043030179j.pdf

## 20200919
- I was fighting Nan from pytorch model.
          - reference: https://tips-memo.com/python-point-loss-nan
          - reference: https://qiita.com/syoamakase/items/a9b3146e09f9fcafbb66


## 20200922
- Extraction of major lesions on CT images.
     - I got below error to prossed CT iamges.
     
     RuntimeError: The following handlers are available to decode the pixel data however they are missing required dependencies: GDCM (req. GDCM)
     
     Solution:
     
     !conda install -c conda-forge python=3.7 -y
     
     !conda install -c conda-forge gdcm -y
     
     import sys
     
     sys.path.append('/usr/local/lib/python3.7/site-packages/')
     
     import gdcm
          
     - reference: https://www.kaggle.com/unforgiven/osic-comprehensive-eda
     - reference: https://www.kaggle.com/c/rsna-intracranial-hemorrhage-detection/discussion/117223
      
  <img width="649" alt="Screen Shot 2020-09-29 at 14 49 26" src="https://user-images.githubusercontent.com/50528980/94608527-1f97ec00-0263-11eb-918a-200d3830000f.png">

## 20200925
- notebooks: 20200926_osci_clustering.ipynb
     - I tried clustering multidimensional time series data.
     - reference: https://rmizutaa.hatenablog.com/entry/2020/09/26/114344
  
<img width="800" alt="Screen Shot 2020-09-29 at 14 14 26" src="https://user-images.githubusercontent.com/50528980/94605143-47d11c00-025e-11eb-8669-75f2b1803013.png">

<img width="808" alt="Screen Shot 2020-09-29 at 14 14 31" src="https://user-images.githubusercontent.com/50528980/94605151-4bfd3980-025e-11eb-81a8-a29e1d812bb6.png">

## 20200927
- Middle Layer Feature Extraction from CT images
     - CT images　→　Keras: mixed7 layrer →　Keras: Global Average Polling layer →　PCA(n_components=100)　→　UMAP(n_components=2)
     - reference: https://speakerdeck.com/metalunk/merukariniokeru-ai-huo-yong-shi-li-pycon-jp-2018?slide=20
     - reference: https://teratail.com/questions/147930
     - reference: https://cpp-learning.com/pca-umap/

<img width="261" alt="Screen Shot 2020-09-29 at 15 35 44" src="https://user-images.githubusercontent.com/50528980/94613139-b9629780-0269-11eb-8072-a1ec9727c80b.png">

- notebooks: 20200927_osci_train-lightgbm.v1.ipynb
     - I tried lightGBM with the data of middle layer feature Extraction from CT images.
     - reference: https://www.kaggle.com/ttahara/osic-baseline-lgbm-with-custom-metric
     
## 20200928
- notebooks: 20200928_bayesian-experiments.v1.ipynb
     - I tried Bayesian Linear Regression model
     - reference: https://www.kaggle.com/carlossouza/bayesian-experiments
     
<img width="613" alt="Screen Shot 2020-09-29 at 15 18 20" src="https://user-images.githubusercontent.com/50528980/94611254-1a3ca080-0267-11eb-863c-de0476495bee.png">

## 20200929
- I started a ”Kaggle diary” based on the following blog.
     - reference: https://zenn.dev/fkubota/articles/3d8afb0e919b555ef068

- notebooks: 20200929-osci-inference-efficientnet-v7.ipynb
     - After using CT imaging, the lowest score at -24.7981 and has not improved.

- notebooks:20200929-osic-baseline-lgbm-with-custom-metric-v2.ipynb
     - Create test dataset with Bayesian approach
     - CV: -6.79467, LB: -7.1484
     - After inferring the test data with a Bayesian approach, we tried using lightGBM, but the results did not improve.
     
<img width="288" alt="Screen Shot 2020-09-29 at 19 48 31" src="https://user-images.githubusercontent.com/50528980/94630971-d6f52880-028c-11eb-99f5-77ddccd4610a.png">

- notebooks:20200929-osic-baseline-lgbm-with-custom-metric-v5.ipynb
     - Create features used based FVC
     - CV: Metric: -6.53430, LB: -7.9569
     - CV is improving, but LB is getting worse.
<img width="388" alt="Screen Shot 2020-09-29 at 22 55 49" src="https://user-images.githubusercontent.com/50528980/94642544-0b2b1200-02aa-11eb-99b5-1b5c17846df8.png">

## 20200930
- 20200929_osci_train-efficientnet.v14.ipynb
     - Create 214 features
     - train_bs = 32, valid_bs = 32, SIZE = 256, Learning_rate = 0.1
     - 20200930_osci_Inference-efficientnet.v8.ipynb
     - CV: Metric: -6.66, LB: -24.7981
     - The LB of regression with CT images is too terrible.

## 20201001
- 202001001_osci_Inference-efficientnet.v10.ipynb
     - 20200929_osci_train-efficientnet.v14.ipynb
     - I tried to fixed submission bugs.
     - But, LB is not improved the -24.7981.
     - reference: https://www.kaggle.com/c/osic-pulmonary-fibrosis-progression/discussion/186683#1027270
<img width="656" alt="Screen Shot 2020-10-01 at 9 33 28" src="https://user-images.githubusercontent.com/50528980/94825066-58eb6b80-03cb-11eb-853e-55e6b90e050d.png">

- 20200929-osic-baseline-lgbm-with-custom-metric-v6.ipynb
     - Add middle layer feature extraction
     - CV Metric: -6.54686, LB: -8.1016
     - reference: https://www.kaggle.com/careyai/inceptionv3-full-pretrained-model-instructions/data

<img width="393" alt="Screen Shot 2020-10-01 at 16 12 42" src="https://user-images.githubusercontent.com/50528980/94864118-22304800-0401-11eb-96b8-4576471ca68a.png">

- 20201001-osic-lgbm-Inference-efficientnet.v2.ipynb
     - Ensemble lgbm 0.8 and effnet 0.2
     - LB -14.9748

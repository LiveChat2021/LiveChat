

## 1. Project Summary
Online communication platforms such as Gitter and Slack play an increasingly critical role in supporting software teamwork, especially for open source development. Conversations on such platforms often contain intensive, valuable information that may be used for better understanding developer communication and collaboration, in order to improve software practices. However, little work has been done in this regard. To bridge the gap, this paper reports a first comprehensive empirical study on developers' live chat data from Gitter. We first collect a large scale of developer daily chat. Then we manually disentangle 749 dialogs, and select the best disentanglement model from four state-of-the-art models for automation, according to their evaluation results. Finally, we perform empirical analysis on live chat aiming to reveal four characteristics: communication profile, community structure, dialog topic, and interaction pattern. In total, we studied 173,278 dialogs, corresponding with 1,402,894 utterances, contributed by 95,416 developers. Major findings include: (1) Developers chat more frequently on workdays than weekends, especially on Wednesday and Thursday; (2) Three social patterns, i.e., constellation, polaris, and galaxy, are observed in live chat communities; (3) Top-3 dialog topics are API usages, errors, and background information; and (4) Six dialog interaction patterns are extracted to guide further improvement. In addition, we provide practical insights on productive dialogs for developers, highlight desired features for platform vendors, and shed light on future research directions. We believe that the findings and insights will enable a better understanding of developers' live chat, as well as a better utilization and mining of knowledge embedded in the massive chat history.

## 2. Study Design

## 3. Results
### 3.1 Experiment on Dialog Disentanglement
### 3.2 RQ1: Communication Profile
### 3.3 RQ2: Community Structure
### 3.4 RQ3: Discussion Topic
This figure shows the distribution of discussion topics in developer live chat. The figure shows discussion topics in gray and their categories in white, as well as the percentages of the corresponding dialogs. The taxonomy expands outwards from higher level categories to lower level categories and topics.
### 3.5 RQ4: Interactive Pattern

## 4. Conclusion

## Images
### (1) DD-test.png
![image](https://github.com/LiveChat2021/LiveChat/blob/main/images/DD-test.png)



## 5. Download
* `data/`
  * `raw/`: original chat history
  * `disentangle/`: chat history after disentangling
  * `manual/`: chat history after manual disentangling

## Content
* [1. Project Summary](#1. Project Summary)
  * `raw/`: original chat history
  * `disentangle/`: chat history after disentangling
  * `manual/`: chat history after manual disentangling

## 1. Project Summary
Online communication platforms such as Gitter and Slack play an increasingly critical role in supporting software teamwork, especially for open source development. Conversations on such platforms often contain intensive, valuable information that may be used for better understanding developer communication and collaboration, in order to improve software practices. However, little work has been done in this regard. To bridge the gap, this paper reports a first comprehensive empirical study on developers' live chat data from Gitter. We first collect a large scale of developer daily chat. Then we manually disentangle 749 dialogs, and select the best disentanglement model from four state-of-the-art models for automation, according to their evaluation results. Finally, we perform empirical analysis on live chat aiming to reveal four characteristics: communication profile, community structure, dialog topic, and interaction pattern. In total, we studied 173,278 dialogs, corresponding with 1,402,894 utterances, contributed by 95,416 developers. Major findings include: (1) Developers chat more frequently on workdays than weekends, especially on Wednesday and Thursday; (2) Three social patterns, i.e., constellation, polaris, and galaxy, are observed in live chat communities; (3) Top-3 dialog topics are API usages, errors, and background information; and (4) Six dialog interaction patterns are extracted to guide further improvement. In addition, we provide practical insights on productive dialogs for developers, highlight desired features for platform vendors, and shed light on future research directions. We believe that the findings and insights will enable a better understanding of developers' live chat, as well as a better utilization and mining of knowledge embedded in the massive chat history.

## 2. Study Design
### 2.1 Research questions
### 2.2 Our Dataset

## 3. Results
### 3.1 Experiment on Dialog Disentanglement
To analyze the dialogs in a large scale, we experiment with the four state-of-art dialog disentanglement approaches, i.e. BiLSTM model, Bert model, E2E model, and FF model. Specifically, we use the manual disentanglement sample data from the previous step as ground truth data, compare and select the best DD model for the purpose of the further analysis in this study. We test the performances of the four approaches on the 749 manually disentangled dialogs, and adopt four widely used clustering metrics for evaluation: Normalized Mutual Information (NMI) , Adjusted Rand Index (ARI) , Shen-F value and F1 score. ARI is a similarity measure between two clusters based on the evaluation to a pairwise basis, while NMI penalizes more on the cluster-level. Shen-F measures how well related utterances are grouped, which is a very common and useful metric for dialogue disentanglement. F1 is the most strict measure which is calculated using the number of perfectly matching conversations.
![image](https://github.com/LiveChat2021/LiveChat/blob/main/images/DD-test.png)
The comparison results are shown in the above figure. The FF approach significantly outperforms the others on disentangling developer live chat. We can see that, FF approach achieves high NMI (avg. 0.74 ) and Shen-F scores (avg. 0.81), and medium-level scores on F1 (avg. 0.47) and ARI (avg. 0.57). Therefore, we select the FF model to disentangle all the utterances of the eight projects. Finally, we use the best FF model to disentangle all the 1,402,894 utterances in chat logs. In total, we obtain 173,278 dialogs.

### 3.2 RQ1: Communication Profile
--------------------Figure
This figure compares the distribution of utterances intensity over 24 hours, across the 8 communities. First, we identify the peak hours of each community in red dashed circles, then highlight the time windows based on the peak hours contained in it with the yellow shade. We can see that, there are three windows of peak hours, which are from UTC 9 to 10, 13 to 14, and 18 to 21. In addition, UTC 1 to 6 corresponds to the low chatting-activity hours. Developers are less active in chatting at that time.
--------------------Figure
This figure shows the distribution of the utterances across different weekdays. We can see that, developers chat more frequently on workdays than on weekends. Noticeably, more developer live chatting happens on Wednesdays and Thursdays than on other weekdays, which possibly corresponds to communication, coordination, and preparation for integration/release/deadline on Fridays.
--------------------Figure
This figure exhibits the distribution of response time calculated from the 173,278 dialogs of the eight communities. The average response time is 220 seconds, the maximum time lag is 1,264 seconds, and the minimum time lag is 2 seconds. The peak point is (23, 393), which means there are 393 dialogs got replies in 23 seconds. We can see that, the time lag largely increases from 0 to 23 seconds, and descend in a long tail. 80% of the dialogs get first responses in 343 seconds. As reported by recent study on Stack Overflow, the threshold of fast answers was 439 seconds. In comparison, live chat gets 50% faster ((439-220)/439) replies than the fast answers in Stack Overflow. Therefore, we consider the responses from live chat are relatively fast.
--------------------Border
Answering RQ1: The peak hours for live chat are from UTC 9 to 10, 13 to 14, and 18 to 21, while UTC 1 to 6 is the low-active hours. Developers are more likely to chat in workdays then weekends, especially in Wednesday and Thursday. Moreover, live chat gets 50% faster replies than the fast answers in Stack Overflow.

### 3.3 RQ2: Community Structure
### 3.4 RQ3: Discussion Topic
This figure shows the distribution of discussion topics in developer live chat. The figure shows discussion topics in gray and their categories in white, as well as the percentages of the corresponding dialogs. The taxonomy expands outwards from higher level categories to lower level categories and topics.
### 3.5 RQ4: Interactive Pattern

## 4. Conclusion
In this paper, we have presented a first large-scale study to gain an empirical understanding of OSS developers' live chat. Based on 1,402,894 utterances taken from eight popular communities on Gitter, we explore the temporal communication profiles of developers, the social networks and their properties towards the community, the taxonomy of discussion topics, and the interaction patterns in live chat. Our study reveals a number of interesting findings and implications including:  (1) There are three social patterns in the OSS community of live chat: polaris network, constellation network, and galaxy network. Constellation networks are the most, followed by polaris networks, galaxy networks are the least; (2) Developers are more likely to chat in workdays than weekends, especially in Wednesday and Thursday; (3) Developers are more active from UTC 9 to 10, 13 to 14, and 18 to 21, corresponding to Central European working time and American working time. The low-active time slice for chatting is Central European and American night; (4) Nearly 1/3 dialogs are about API usage. Developers discuss more about errors, unwanted behaviors and do-not-work, than reliability issues, performance issues, and test/build failures; (5) There are six interaction patterns identified in live chat: exploring solution, clarifying answer, clarifying question, direct/discussed answer, self-answered monologue, and unanswered monologue; and (6) We provide guidelines for developers in live chat, highlight advanced features for online communication platform vendors, and provoke insightful future research questions for OSS researchers. In future, we plan to investigate how well can we automatically classify the dialogs into different topics, as well as attempt to construct knowledge bases according to already answered questions and their corresponding solutions from live chat.
We hope that the findings and insights that we have uncovered will help drive future research into a more in-depth understanding of OSS development collaboration and a better utilization and mining of knowledge embedded in massive chat history. To facilitate replications or other types of future work, we provide the utterance data and disentangled dialogs used in this study online: https://github.com/LiveChat2021/LiveChat.



## 5. Download
* `data/`
  * `raw/`: original chat history
  * `disentangle/`: chat history after disentangling
  * `manual/`: chat history after manual disentangling

## Content
[1 Project Summary](#1-project-summary)<br>
[2 Study Design](#2-study-design)<br>
&ensp;&ensp;[2.1 Research Questions](#21-research-questions)<br>
&ensp;&ensp;[2.2 Our Dataset](#22-our-dataset)<br>
[3 Results](#3-results)<br>
&ensp;&ensp;[3.1 Experiment on Dialog Disentanglement](#31-experiment-on-dialog-disentanglement)<br>
&ensp;&ensp;[3.2 RQ1: Communication Profile](#32-rq1-communication-profile)<br>
&ensp;&ensp;[3.3 RQ2: Community Structure](#33-rq2-community-structure)<br>
&ensp;&ensp;[3.4 RQ3: Discussion Topic](#34-rq3-discussion-topic)<br>
&ensp;&ensp;[3.5 RQ4: Interactive Pattern](#35-rq4-interactive-pattern)<br>
[4 Conclusion](#4-conclusion)<br>
[5 Download](#5-download)<br>

## 1 Project Summary
&ensp;&ensp;Online communication platforms such as Gitter and Slack play an increasingly critical role in supporting software teamwork, especially for open source development. Conversations on such platforms often contain intensive, valuable information that may be used for better understanding developer communication and collaboration, in order to improve software practices. However, little work has been done in this regard. To bridge the gap, this paper reports a first comprehensive empirical study on developers' live chat data from Gitter. We first collect a large scale of developer daily chat. Then we manually disentangle 749 dialogs, and select the best disentanglement model from four state-of-the-art models for automation, according to their evaluation results. Finally, we perform empirical analysis on live chat aiming to reveal four characteristics: communication profile, community structure, dialog topic, and interaction pattern. In total, we studied 173,278 dialogs, corresponding with 1,402,894 utterances, contributed by 95,416 developers. Major findings include: (1) Developers chat more frequently on workdays than weekends, especially on Wednesday and Thursday; (2) Three social patterns, i.e., constellation, polaris, and galaxy, are observed in live chat communities; (3) Top-3 dialog topics are API usages, errors, and background information; and (4) Six dialog interaction patterns are extracted to guide further improvement. In addition, we provide practical insights on productive dialogs for developers, highlight desired features for platform vendors, and shed light on future research directions. We believe that the findings and insights will enable a better understanding of developers' live chat, as well as a better utilization and mining of knowledge embedded in the massive chat history.

## 2 Study Design
### 2.1 Research Questions
* RQ1 (Communication Habits): Are there common habits in developers' usage of live-chatting? 
* RQ2 (Community Structure): What are the structural characteristics of social network built from developer live chat data? 
* RQ3 (Dialog Topic): What are the primary topic types frequently discussed by developer in live chat? 
* RQ4 (Interaction Pattern): How developers interact with each other? 

### 2.2 Our Dataset
![image](https://github.com/LiveChat2021/LiveChat/blob/main/images/table-ourdata.png)<br>

## 3 Results
### 3.1 Experiment on Dialog Disentanglement
&ensp;&ensp;To analyze the dialogs in a large scale, we experiment with the four state-of-art dialog disentanglement approaches, i.e. BiLSTM model, Bert model, E2E model, and FF model. Specifically, we use the manual disentanglement sample data from the previous step as ground truth data, compare and select the best DD model for the purpose of the further analysis in this study. We test the performances of the four approaches on the 749 manually disentangled dialogs, and adopt four widely used clustering metrics for evaluation: Normalized Mutual Information (NMI) , Adjusted Rand Index (ARI) , Shen-F value and F1 score. ARI is a similarity measure between two clusters based on the evaluation to a pairwise basis, while NMI penalizes more on the cluster-level. Shen-F measures how well related utterances are grouped, which is a very common and useful metric for dialogue disentanglement. F1 is the most strict measure which is calculated using the number of perfectly matching conversations.<br>
<div align=center><img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/DD-test.png" width="600" alt="dd-test"/></div><br>
&ensp;&ensp;The comparison results are shown in the above figure. The FF approach significantly outperforms the others on disentangling developer live chat. We can see that, FF approach achieves high NMI (avg. 0.74 ) and Shen-F scores (avg. 0.81), and medium-level scores on F1 (avg. 0.47) and ARI (avg. 0.57). Therefore, we select the FF model to disentangle all the utterances of the eight projects. Finally, we use the best FF model to disentangle all the 1,402,894 utterances in chat logs. In total, we obtain 173,278 dialogs.

### 3.2 RQ1: Communication Profile
<div align=center><img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/hours.png" width="600" alt="hours"/></div><br>
&ensp;&ensp;This figure compares the distribution of utterances intensity over 24 hours, across the 8 communities. First, we identify the peak hours of each community in red dashed circles, then highlight the time windows based on the peak hours contained in it with the yellow shade. We can see that, there are three windows of peak hours, which are from UTC 9 to 10, 13 to 14, and 18 to 21. In addition, UTC 1 to 6 corresponds to the low chatting-activity hours. Developers are less active in chatting at that time.
<div align=center><img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/days.png" width="600" alt="days"/></div><br>
&ensp;&ensp;This figure shows the distribution of the utterances across different weekdays. We can see that, developers chat more frequently on workdays than on weekends. Noticeably, more developer live chatting happens on Wednesdays and Thursdays than on other weekdays, which possibly corresponds to communication, coordination, and preparation for integration/release/deadline on Fridays.<br>
<div align=center><img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/timelag.png" width="600" alt="timelag"/></div><br>
&ensp;&ensp;This figure exhibits the distribution of response time calculated from the 173,278 dialogs of the eight communities. The average response time is 220 seconds, the maximum time lag is 1,264 seconds, and the minimum time lag is 2 seconds. The peak point is (23, 393), which means there are 393 dialogs got replies in 23 seconds. We can see that, the time lag largely increases from 0 to 23 seconds, and descend in a long tail. 80% of the dialogs get first responses in 343 seconds. As reported by recent study on Stack Overflow, the threshold of fast answers was 439 seconds. In comparison, live chat gets 50% faster ((439-220)/439) replies than the fast answers in Stack Overflow. Therefore, we consider the responses from live chat are relatively fast.<br>

&ensp;&ensp;**Answering RQ1**: The peak hours for live chat are from UTC 9 to 10, 13 to 14, and 18 to 21, while UTC 1 to 6 is the low-active hours. Developers are more likely to chat in workdays then weekends, especially in Wednesday and Thursday. Moreover, live chat gets 50% faster replies than the fast answers in Stack Overflow.

### 3.3 RQ2: Community Structure
![image](https://github.com/LiveChat2021/LiveChat/blob/main/images/table-network.jpg)<br>
&ensp;&ensp;This table shows the social network properties of the eight communities. Init.%, Resp.%, and Both% denote the percentage of developers serving the role of dialog initiators, respondents, and both. Intuitively, we consider that respondents share their knowledge to others, while initiators receive knowledge from others. We can see that, the four communities (Appium, Docker, Gitter, and Ethereum) belong to galaxy and polaris networks have higher percentage (75.04%-81.70%) of dialog initiators and lower percentage (18.30%-24.96%) of respondents/both. The high percentage of dialog initiators may relate to the application nature of the open source projects, e.g., Ethereum is one of the most widely open-source blockchain system, thus there is a large number of users acquire technical support from live chat. While the other four communities (Angular, DL4J, Nodejs, and Typescript) have higher percentage (29.94%-48.62%) of respondents/both. A possible explanation is that these four projects are more widely used for development purpose, e.g., angular is a platform for building mobile and desktop web applications, therefore, such communities appear to be knowledge-sharing and collaborative.<br>
<img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/angular.png" width="400" height="400" alt="angular"/>
<img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/appium.png" width="400" height="400" alt="appium"/><br>
<img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/docker.png" width="400" height="400" alt="docker"/>
<img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/eclipse.png" width="400" height="400" alt="eclipse"/><br>
<img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/ethereum.png" width="400" height="400" alt="ethereum"/>
<img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/gitter.png" width="400" height="400" alt="gitter"/><br>
<img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/microsoft.png" width="400" height="400" alt="microsoft"/>
<img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/nodejs.png" width="400" height="400" alt="nodejs"/><br>
&ensp;&ensp;The above figures show the social network visualizations of the eight communities generated by Gephi. Each node represents one developer, and the edge denotes the dialog relationship between two developers. We color the vertex of initiator with blue, the vertex of respondent with yellow, and the vertex of both roles with red. In addition, the node’s size indicates its corresponding degree. Based on the observation on community structures, we categorize the 8 communities into three groups, consisting of:
* Polaris networkis a type of highly centralized network where the community is organized around its single focal point.
* Constellation network is a type of moderately centralized network where the community is organized around its multiple focal points. 
* Galaxy network is a type of decentralized network where all individuals in the community have similar relationships.<br>

&ensp;&ensp;The 4 communities on the top (i.e., Angular, DL4J, NodeJS, and Typescript) belong to the constellation network, i.e., moderately centralized network. 3 communities i.e., Appium, Docker, and Gitter) belong to the polaris network, i.e., highly centralized network. The remaining Ethereum community belongs to the galaxy network, i.e., decentralized network.<br>
&ensp;&ensp;**Answering RQ2**: By visualizing social networks of eight studied communities, we identify three social network structures for developers' live chat. Half of the communities (4/8) are constellation networks. A minority of the communities (3/8) are polaris networks. Only one community belongs to galaxy network. In comparison, we find that developers in live chat may have less influence than developers in email in spreading information, but have a more closely connected community than that from email.

### 3.4 RQ3: Discussion Topic
<div align=center><img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/donut.png" width="600" alt="donut"/></div><br>
&ensp;&ensp;This figure shows the distribution of discussion topics in developer live chat. The figure shows discussion topics in gray and their categories in white, as well as the percentages of the corresponding dialogs. The taxonomy expands outwards from higher level categories to lower level categories and topics.<br>
<div align=center><img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/table-topic.png" alt="topic"/></div><br>
&ensp;&ensp;This table shows the descriptions of categories. The orange cells are decomposed from "Discrepancy", and the green cells are decomposed from "Conceptual". <br>
<div align=center><img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/donut-sort.png" alt="topic"/></div><br>
&ensp;&ensp;The above figure shows the ranking of topics. For each topic, we provide an example from the real-world live chat. <br>

* API usage: How to know if the keyboard is open or not
[2016-12-01 11:32:22] <deepakchoudhury> I have a doubt.hide_keyboard is working great but do you know how to know if the keyboard is open or not<br>
[2016-12-01 11:32:38] <deepakchoudhury> for andorid app<br>
[2016-12-01 12:46:38] <pramodnaik> Hi@deepakchoudhury@deepakchoudhury: I don't think u have an option to check if keyboard is opened or not. But u can try catch the hide keyboard. If it throws exception means keyboard is already closed<br>
[2016-12-01 13:53:26] <deepakchoudhury> Thanks@pramodnaik...its working...<br>

* Error: I getError: No such image
[2016-11-28 21:25:01] <mikewrighton> I getError: No such image, container or task: a9952be2c74f2c6f3a7ae9faf12dc1576367bba5197fe74c243b637289fb653b<br>
[2016-11-28 21:25:16] <mikewrighton> but an exec id is not an image, container or task<br>
[2016-11-28 21:26:05] <mikewrighton> so docker inspect, as far as I can tell, does not support quering exec ids<br>
[2016-11-28 22:53:10] <dragon788> mikewrighton: I think you are correct, inspect is mostly for containers and images<br>
 
&ensp;&ensp;**Answering RQ3**: Developers launch solution-oriented dialogs and problem-oriented dialogs more than knowledge-oriented dialogs. Nearly 1/3 dialogs are about API usage. Developers discuss more about error, unwanted behavior and do-not-work, than reliability issue, performance issue, and test/build failure.

### 3.5 RQ4: Interactive Pattern
<div align=center><img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/patterns.png" width="600" alt="patterns"/></div><br>
&ensp;&ensp;This figure illustrates the six interaction patterns in live chat, constructed using open card sorting. This figure shows dialog initiators in blue nodes, respondents in yellow nodes. The lines denote the reply-to relationships, and the labels represent developer intents in this table.<br>
<div align=center><img src="https://github.com/LiveChat2021/LiveChat/blob/main/images/table-intent.png" alt="intent"/></div><br>
&ensp;&ensp;In this work, we identify the following six interaction patterns:<br>

* P1: Exploring Solutions. Given the original questions posted by dialog initiator, other developers provide possible answers. But the initiator gives negative feedback indicating these answers do not address the question. When the correct answer is posted, the initiator gives positive feedback and end the dialog. 
* P2: Clarifying Answer. Given the original questions posted by dialog initiator, other developer provides a possible answer. Then the initiator posts follow-up questions to clarify the answer until the initiator fully understands. 
* P3: Clarifying Question. Given the original questions posted by dialog initiator, the respondent requires the initiator to clarify the question in more details until he fully understands. Then the respondent posts his answer, and the initiator gives feedback or greetings.
* P4: Direct/Discussed Answer. Given the original questions posted by dialog initiator, the respondent directly gives an answer, or gives the answer after an internal discussion.  
* P5: Self-answered Monologue. The original questions posted by dialog initiator are answered by himself. 
* P6: Unanswered Monologue. The original questions posted by dialog initiator are not answered.

&ensp;&ensp;**Answering RQ4**: Six interaction patterns are identified in live chat: exploring solutions, clarifying answer, clarifying question, direct/discussed answer, self-answered monologue, and unanswered monologue. The direct/discussed answer pattern takes the largest proportions in most of communities. There are still 1/4 dialogs that did not get responses on average. Dialogs belong to Exploring Solutions pattern last the longest time than others. 

## 4 Conclusion
&ensp;&ensp;In this paper, we have presented a first large-scale study to gain an empirical understanding of OSS developers' live chat. Based on 1,402,894 utterances taken from eight popular communities on Gitter, we explore the temporal communication profiles of developers, the social networks and their properties towards the community, the taxonomy of discussion topics, and the interaction patterns in live chat. Our study reveals a number of interesting findings and implications including:  (1) There are three social patterns in the OSS community of live chat: polaris network, constellation network, and galaxy network. Constellation networks are the most, followed by polaris networks, galaxy networks are the least; (2) Developers are more likely to chat in workdays than weekends, especially in Wednesday and Thursday; (3) Developers are more active from UTC 9 to 10, 13 to 14, and 18 to 21, corresponding to Central European working time and American working time. The low-active time slice for chatting is Central European and American night; (4) Nearly 1/3 dialogs are about API usage. Developers discuss more about errors, unwanted behaviors and do-not-work, than reliability issues, performance issues, and test/build failures; (5) There are six interaction patterns identified in live chat: exploring solution, clarifying answer, clarifying question, direct/discussed answer, self-answered monologue, and unanswered monologue; and (6) We provide guidelines for developers in live chat, highlight advanced features for online communication platform vendors, and provoke insightful future research questions for OSS researchers. In future, we plan to investigate how well can we automatically classify the dialogs into different topics, as well as attempt to construct knowledge bases according to already answered questions and their corresponding solutions from live chat.<br>
&ensp;&ensp;We hope that the findings and insights that we have uncovered will help drive future research into a more in-depth understanding of OSS development collaboration and a better utilization and mining of knowledge embedded in massive chat history. To facilitate replications or other types of future work, we provide the utterance data and disentangled dialogs used in this study online: https://github.com/LiveChat2021/LiveChat.

## 5 Download
* `data/`
  * `raw/`: original chat history
  * `disentangle/`: chat history after disentangling
  * `manual/`: chat history after manual disentangling

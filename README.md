## File organization
* `data/`
  * `raw/`: original chat history
  * `disentangle/`: chat history after disentangling
  * `manual/`: chat history after manual disentangling
* `images/`
  * `dd-test.png`: The comparison results are shown in Figure dd-test. The FF approach significantly outperforms the others on disentangling developer live chat. We can see that, FF approach achieves high NMI (avg. 0.74 ) and Shen-F scores (avg. 0.81), and medium-level scores on F1 (avg. 0.47) and ARI (avg. 0.57). Therefore, we select the FF model to disentangle all the utterances of the eight projects. 

## Images
### (1) DD-test.png
![image](https://github.com/LiveChat2021/LiveChat/blob/main/images/DD-test.png)
ARI is a similarity measure between two clusters based on the evaluation to a pairwise basis, while NMI penalizes more on the cluster-level.
Shen-F measures how well related utterances are grouped, which is a very common and useful metric for dialogue disentanglement.
F1 is the most strict measure which is calculated using the number of perfectly matching conversations.
The comparison results are shown in Figure dd-test. The FF approach significantly outperforms the others on disentangling developer live chat. We can see that, FF approach achieves high NMI (avg. 0.74 ) and Shen-F scores (avg. 0.81), and medium-level scores on F1 (avg. 0.47) and ARI (avg. 0.57). Therefore, we select the FF model to disentangle all the utterances of the eight projects. 

### (2) Network
#### Angular
![image](https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/angular.png)
#### Appium
![image](https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/appium.png)
#### Docker
![image](https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/docker.png)
#### Eclipse
![image](https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/eclipse.png)
#### Ethereum
![image](https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/ethereum.png)
#### Gitter
![image](https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/gitter.png)
#### Microsoft
![image](https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/microsoft.png)
#### Nodejs
![image](https://github.com/LiveChat2021/LiveChat/blob/main/images/RQ1/nodejs.png)


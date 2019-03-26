# GAN Lecture

## 1주차
### MLE (Maximum Likelihood Estimation)
(참고자료) 
 - http://sanghyukchun.github.io/58/  ***
 - http://rstudio-pubs-static.s3.amazonaws.com/204928_c2d6c62565b74a4987e935f756badfba.html
 - http://arkainoh.blogspot.kr/2017/10/parametric.learning.maximum.likelihood.estimation.html
### GMM (Gaussian Mixture Model) 
(참고자료)
 - http://3months.tistory.com/154 ***
 - http://iskim3068.tistory.com/52
 - https://m.blog.naver.com/PostView.nhn?blogId=kmkim1222&logNo=10187825620&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F
### 기타 추천 독서 목록 (Optional)
세상에서 가장 쉬운 베이즈통계학 입문 독서: 확률이론만으로 한학기 수업 분량이 될 수 있지만, 저희 수업에서 필요한 확률론은 “세상에서 가장 쉬운 베이즈통계학 입문”를 읽어보시면 어느정도 (속성으로) 해결 될것이라 생각합니다. 이 책보다 쉽게 설명한 책이 없다고 해도 과언이 아니라고 개인적으로 생각합니다. 읽어보시면 앞으로 강의를 이해하시는데 분명 큰 도움이 될것이라 생각하니, 강의가 진행되는 동안 틈틈히 읽어보시는 것을 권장드립니다. 시간이 부족하신 분들은 다음 자료를 참고하셔서 확률이론을 리뷰하고 오시면 좋을 것 같습니다. 
 - (https://see.stanford.edu/materials/aimlcs229/cs229-prob.pdf)***

## 2주차
### 정보이론 예습: 
VAE뿐만 아니라 GAN을 이해하기 위해서도 필요한 내용들입니다. 기초적인 내용은 함께 학습 할 예정입니다. 큰 그림을 이해하기 위해서 다음의 (7분) 동영상을 꼭 시청하시길 부탁드립니다 
 - (칸아카데미 정보이론 동영상: https://ko.khanacademy.org/computing/computer-science/informationtheory/moderninfotheory/v/information-entropy)***
### (Optional) 정보이론 한글 자료: 
 - http://newsight.tistory.com/119, http://sanghyukchun.github.io/62/
### (Optional) 세상에서 가장 쉬운 베이즈통계학 입문을 다 읽으신 분들은 다음 자료를 참고하셔서 이론을 한번 더 리뷰해보시면 좋을 것 같습니다. 
 - (http://norman3.github.io/prml/docs/chapter01/2, https://see.stanford.edu/materials/aimlcs229/cs229-prob.pdf) 
### (Optional) Variational Inference 

## 3주차
 - http://nolsigan.com/blog/what-is-variational-autoencoder/ (한글) ***
 - http://kvfrans.com/variational-autoencoders-explained/#disqus_thread (영어) 개요가 간단하게 설명 잘 되어 있습니다. ***
 - http://jaejunyoo.blogspot.com/2017/04/auto-encoding-variational-bayes-vae-1.html (한글) 재준님 블로그 (내용을 처음 접하시는 분들에게는 설명이 다소 어려울 수 있습니다.)
또한, 이번시간에 주요하게 다룰 내용들의 상세한 내용은 다음 논문에서 확인 할 수 있습니다.
아래 내용은 수업전에 보시지 않으셔도 되지만, VAE를 더욱 잘 이해하시고 싶으신 분들은 수업 이후라도 읽어보시고, 
잘 이해가지 않는 부분에 대해서는 온라인 및 오프라인을 통해 질문해주시면 답변 드리겠습니다.  :)
 - Tutorial on Variational Auto-encoder (https://arxiv.org/abs/1606.05908) 
 - Auto-Encoding Variational Bayes (https://arxiv.org/abs/1312.6114)
 - Semi-Supervised Learning with Deep Generative Models (https://arxiv.org/abs/1406.5298)

## 4주차
GAN의 경우 이론적인 내용은 VAE에 비해 약간 쉬운편입니다. 하지만, 학습과정에 이론적으로 불안전한 부분이 있어서 실제 구현 이슈가 좀 더 있는 편입니다. 
지난 시간까지 다소 수식이 많고 어려운 이론적인 강의를 같이 잘 들어 주셔서, 다음 강의 부터는 강의가 좀 더 원활하게 진행되지 않을까 생각합니다. 
다음 수업에서는 GAN의 기초 부터 시작해서, GAN의 장단점, VAE와의 비교, 기타 Trick 들에 대해서 이야기 나눠 봅시다. 수업시간에 메인으로 참고할 자료는 GAN의 저자인 Ian Goodfellow 가 작성한 “NIPS 2016 Tutorial: Generative Adversarial Networks”을 메인으로 하겠습니다. 
 -  https://arxiv.org/abs/1701.00160 (영상 자료: https://www.youtube.com/watch?v=AJVyzd0rqdc) GAN을 완전히 처음 접하시는 분들은 유재준님이 한글로 잘 정리해주신 블로그가 있으니 참고하셔서 GAN에 대한 약간의 감을 익히시면 좋을것 같습니다.
 - 한글자료: http://jaejunyoo.blogspot.com/2017/01/generative-adversarial-nets-1.html 혹시 기존 CNN의 Convolutional Operation에 익숙하지 않으신 분들은 https://tensorflow.blog/a-guide-to-convolution-arithmetic-for-deep-learning/ 를 참고하셔서 Convolution연산에 대해서도 리뷰를 해오시면 좋을것 같습니다. 특히, Generator 부분을 구현하는 “Transpose Convolution Layer (Deconvolution Layer)”부분을 살펴보시는 것이 도움이 같습니다. 


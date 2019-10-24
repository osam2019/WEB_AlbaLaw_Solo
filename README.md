# WEB_AlbaLaw_Solo
노동자들이 일자리에서의 인권을 지켜나갈 수 있게 도와주는 챗복 및 웹사이트

관등성명: 일병 전호영

# 알바로
노동력이 국가의 발전과 생산력에 큰 기여를 하는 것은 잘 알려진 사실입니다. 하지만 근로자들의 효율성과 생산력을 유지하기 위해서는 반드시 인권과 일에 대한 마땅한 보상이 보장되어야 합니다. 저는 국가의 기초가 되는 노동자들이 본인들의 배경과 상관없이 일자리에서의 인권을 지켜나갈 수 있게 도와주는 웹사이트를 구축하고 싶은 마음에, 누구나 24/7 접근 가능하며, 개인의 상황을 다른 사람에게 알리지 않고도 상황에 맞는 즉각적인 해답을 얻을 수 있는 편리한 법률 챗봇 서비스 구현을 시도해 봤습니다.
챗봇은 퇴직금, 임금, 초과근무, 부당해고 등 다양한 문제를 다루는 노동 변호사 챗봇을 탑재해 사용자에게 부담 없는 간단한 노동법 지식에 대한 자문을 구할 수 있도록 만들었습니다. 챗봇은 각각 분야에 알맞은 질문들을 사용자에게 보여주고 사용자의 답장을 받아 문서를 작성하거나 근로법 위반 여부 등을 간략하고 신속하게 확인해줄 겁니다 (문서작성 기능은 아직 완성하지 못한 상황입니다).
다이알로그 플로우와 AWS Lambda를 이용해 카카오톡과 웹사이트로 REST API를 제공하고 사용자 요구에 따라 시나리오에 따라 답장을 하거나 사용자 메시지를 RDS에 저장합니다. 웹사이트는 Vue JS로 구현했습니다.
소스코드는 albamemo 폴더 안에 있습니다.
### Prerequisites


알바로 프론트엔드(웹)를 구현 시작하기 위해서는 다음을 install했습니다:

Vue.js
```
npm install -g @vue/cli
# OR
yarn global add @vue/cli

```
Vue.js 환경에서의 챗봇 웹사이트 프론트엔드 개발을 위해서는 vue-chat-widget와
```
npm install vue-chat-widget
```

axios를 사용했습니다.

```
npm install axios
```
### Installation Process

주소를 복사해 git clone하셔서 

```
cd albamemo
npm install
```

##Getting Started

```
npm run serve
```
하시면 localhost:8080에 웹사이트가 띄워집니다.

## Running tests

웹사이트에서 말풍선 버튼을 누른뒤 “내사업장 근로기준법 준수 여부”를 입력하시고 답장으로 “어느 분야의 근로기준법 위반여부를 확인하시겠습니까?”라는 문구가 나오는지 확인 하십시오.



### Known Issues

챗봇은 AWS API GATEWAY와 AWS RDS를 이용하기 때문에 둘중에 하나라도 정상적으로 작동하지 않으면 챗봇도 작동이 안됩니다.
챗봇은 아직 개발중이라 받을수 있는 질문과 답의 형태 및 내용이 한정되어있습니다. 사업장 환경을 체크해주는 “내사업장 근로기준법 준수 여부”에서는 가끔씩 올바른 답장이 안나올수도 있습니다 (시간상 문제로 모든 버그를 잡지 못함). 
 
### Troubleshooting

common solutions:
*웹사이트 refresh
*채팅창에 ‘나가기’ 입력
*API 문제가 있으면 기다리기…

## Built With

* Vue - The web framework used
* Axios 
* AWS Lambda
* Dialogflow
* AWS RDS

### Contact Information

hj878@nyu.edu

## Acknowledgments

* https://www.npmjs.com/package/vue-chat-widget

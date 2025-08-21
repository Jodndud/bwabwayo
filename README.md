![bwabwayo](/Thumbnail.png)

## 📝 프로젝트 개요
비대면 화상 중고거래 플랫폼 **봐봐요**는 실시간 화상 채팅을 통한 거래 검증으로 **택배거래 사기 문제를 예방**하고, 안전하고 신뢰성 있는 중고거래 환경을 제공합니다.
- **개발 기간** : 2025.07.07 ~ 2025.08.18 (7주)
- **플랫폼** : Web
- **개발 인원** : 6명 (프론트엔드 2명, 백엔드 4명)
  
## 🛠 사용 기술
### FE
![Next.js](https://img.shields.io/badge/Next.js-14-black?style=for-the-badge&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5.5.3-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![Zustand](https://img.shields.io/badge/Zustand-5.0.6-purple?style=for-the-badge)
![Axios](https://img.shields.io/badge/Axios-1.11.0-671ddf?style=for-the-badge)
![OpenVidu](https://img.shields.io/badge/OpenVidu_Browser-2.29.0-blue?style=for-the-badge)
![STOMP](https://img.shields.io/badge/STOMP.js-7.1.1-yellow?style=for-the-badge)
![SockJS](https://img.shields.io/badge/SockJS-1.6.1-orange?style=for-the-badge)
![Socket.io](https://img.shields.io/badge/Socket.io-4.8.1-black?style=for-the-badge&logo=socketdotio)
![TossPayments](https://img.shields.io/badge/TossPayments_SDK-2.3.5-blue?style=for-the-badge)
![Swiper](https://img.shields.io/badge/Swiper-11.2.10-6332f6?style=for-the-badge)
![React Slick](https://img.shields.io/badge/React_Slick-0.30.3-61dafb?style=for-the-badge&logo=react)
![React Calendar](https://img.shields.io/badge/React_Calendar-6.0.0-ff6f61?style=for-the-badge)
![React Date Picker](https://img.shields.io/badge/React_Date_Picker-12.0.1-5a9bd3?style=for-the-badge)
![Lucide React](https://img.shields.io/badge/Lucide_React-0.539.0-0f172a?style=for-the-badge)

---

### BE
![Java](https://img.shields.io/badge/Java-17-007396?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.5.3-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-green?style=for-the-badge&logo=springsecurity&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=jsonwebtokens)
![Spring Data JPA](https://img.shields.io/badge/Spring_Data_JPA-6DB33F?style=for-the-badge)
![Redis](https://img.shields.io/badge/Redis-7.2-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-8.0.18-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Qdrant](https://img.shields.io/badge/Qdrant-1.15.1-FF4B4B?style=for-the-badge&logo=qdrant&logoColor=white)
![QueryDSL](https://img.shields.io/badge/QueryDSL-5.0.0-00599C?style=for-the-badge)
![Spring Cloud AWS](https://img.shields.io/badge/Spring_Cloud_AWS-2.2.6-ffca28?style=for-the-badge)
![SpringDoc OpenAPI](https://img.shields.io/badge/OpenAPI-2.8.8-6BA539?style=for-the-badge&logo=openapiinitiative&logoColor=white)
![Lombok](https://img.shields.io/badge/Lombok-red?style=for-the-badge)

---

### DevOps
![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04.4_LTS-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-1.18.0-009639?style=for-the-badge&logo=nginx&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-28.3.2-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Docker Compose](https://img.shields.io/badge/Docker_Compose-v2.38.2-003f8c?style=for-the-badge&logo=docker&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-2.516.1-D24939?style=for-the-badge&logo=jenkins&logoColor=white)

---

### Collaboration
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitLab](https://img.shields.io/badge/GitLab-orange?style=for-the-badge&logo=gitlab&logoColor=white)
![Notion](https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white)
![Mattermost](https://img.shields.io/badge/Mattermost-0058CC?style=for-the-badge&logo=mattermost&logoColor=white)
![Discord](https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)
![Figma](https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white)
![Jira](https://img.shields.io/badge/Jira-0052CC?style=for-the-badge&logo=jira&logoColor=white)


## 📊 시스템 구조
[시스템 구조도 이미지]

## 🔍 주요 기능
1. 실시간 채팅 기능
  메세지 타입에 따라 다른 공지글을 보내줘야하기 때문에 WebSocket을 기반으로 STOMP 프로토콜 사용
  ```
  [STOMP연결] - [STOMP Client연결] - [STOMP 구독] - [메시지 송/수신]
  ```

2. WebRTC를 통한 화상공유
 OpenVidu 라이브러리를 이용해 실시간 공유 단순화
 ```typeScript
 // OpenVidu-React 예제의 toekn helpers 부분 수정 -> 동작 확인
 // -------- token helpers --------
  async function getToken() {
    const sessionId = await createSession(state.mySessionId);
    return await createToken(sessionId);
  }
  async function createSession(sessionId: string) {
    if (videoSessionId) {
      console.log('기존 세션ID 사용:', videoSessionId);
      return videoSessionId;
    }
    const res = await axios.post(`${baseUrl}/api/sessions`, { videoRoomId: sessionId }, { headers: { 'Content-Type': 'application/json' } });
    return res.data;
  }
  async function createToken(sessionId: string) {
    const res = await axios.post(`${baseUrl}/api/sessions/${sessionId}/token`, {}, { headers: { 'Content-Type': 'application/json' } });
    return res.data;
  }
 ```

## 📁 프로젝트 구조
### 라우트 구조 (App Router)
```
app/
├── page.tsx (홈페이지)
├── layout.tsx
├── globals.css
├── signup/ (회원가입)
├── logincallback/ (로그인 콜백)
├── search/ (검색)
├── product/ (상품 등록, 수정, 상세)
├── shop/ (상점 페이지)
├── chat/ (채팅 목록, 채팅방, 결제 성공)
├── mypage/ (마이페이지)
├── cs-center/ (고객센터)
├── admin/ (관리자 페이지)
└── test/ (시스템 메시지 테스트)
```

### Store 구조 (Zustand)
```
stores/
├── auth/ (로그인/로그아웃, 사용자 인증 상태)
├── chatting/ (채팅방 관리, 메시지 처리, 화상예약, 타입별 메시지)
├── product/ (상품 CRUD, 상품 목록 관리 / 좋아요 상태 관리)
├── mypage/ (사용자 활동 내역)
├── admin/ (관리자 조회, 답변)
├── cs-store/ (신고, 문의 CRUD)
├── ai/ (AI 상품 설명 생성)
├── shop/ (상점 정보 관리)
├── user/ (사용자 정보 관리)
├── modalStore.ts (모달 상태 관리)
├── loadingStore.ts (로딩 상태 관리)
├── notificationStore.ts (알림 관리)
├── signUpStore.ts (회원가입 프로세스)
├── chatBotStore.ts (챗봇 상태 관리)
├── imageUploadStore.ts (이미지 업로드 관리)
└── categoryStore.ts (카테고리 관리)
```

## 이슈
1. 채팅방의 많은 기능으로 인해 실시간 메시지 송수신 오류
- 해결방안: 많은 라우트 요청으로 인해 구독이 끊어져 재연결 요청 및 구독 코드 추가
```typeScript
// 5초마다 클라이언트 재연결
const client = new StompJs.Client({
  webSocketFactory: () => socket,
  connectHeaders: {
    Authorization: `Bearer ${accessToken}`,
  },
  reconnectDelay: 5000,  // ← 자동 재연결 지연 시간 (5초)
  heartbeatIncoming: 4000,
  hear독
const subs = get()._roomSubs;
Object.keys(subs).forEach((rid) => {
  const ridNum = Number(rid);
  if (!Number.isNaN(ridNum)) {
    try {
      get().subscribeToRoom(ridNum);
    } catch (e) {
      console.error('재구독 실패:', ridNum, e);
    }
  }
})
```

2. 개발환경에서의 경로(이미지 등) 관리
- 해결방안: 환경변수 설정(방법1: .env파일 생성(추천), 방법2: next.config.mjs 파일에서 간단히 생성)
```javaScript
// next.config.mjs
const nextConfig = {
  env: {
    NEXT_PUBLIC_PUBLIC_URL: process.env.NODE_ENV === 'production' ? '/fe' : '',
    NEXT_PUBLIC_API_URL: 'https://baseurl.co.kr/api/'
  },
```
```env
# .env
NEXT_PUBLIC_PUBLIC_URL=fe
NEXT_PUBLIC_API_URL=https://baseurl.co.kr/api
```
사용
```typeScript
const baseUrl = process.env.NEXT_PUBLIC_PUBLIC_URL

export default class Compoenent(){
  return(
    <div>
      <img src=`${baseUrl}/images/sample.png` alt="sample" />
    </div>
  )
}
```

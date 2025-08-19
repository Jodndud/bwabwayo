## 📝 프로젝트 소개
화상거래를 통한 중고거래 플랫폼(봐봐요) 프론트서버

## 🛠 사용 기술
![Next.js](https://img.shields.io/badge/Next.js-14-black?style=for-the-badge&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![STOMP](https://img.shields.io/badge/STOMP-WebSocket-yellow?style=for-the-badge)
![OpenVidu](https://img.shields.io/badge/OpenVidu-2.28.0-blue?style=for-the-badge)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![Zustand](https://img.shields.io/badge/Zustand-4.4.7-purple?style=for-the-badge)

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
   - 해결방안

2. 개발환경에서의 이미지 주소 관리
    - 해결방안 : 환경변수 설정(방법1: .env파일 생성(추천), 방법2: next.config.mjs 파일에서 간단히 생성)
      ```javaScript
      // next.config.mjs
      const nextConfig = {
        env: {
          NEXT_PUBLIC_PUBLIC_URL: process.env.NODE_ENV === 'production' ? '/fe' : '',
          NEXT_PUBLIC_API_URL: 'https://baseurl.co.kr/api/'
        },
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

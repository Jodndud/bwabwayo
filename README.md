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

3. WebRTC를 통한 화상공유
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

4. ㄴ

## 프로젝트 구조
<details>
  <summary>📁 라우트 구조 (App Router)</summary>
  app/
  ├── page.tsx (홈페이지)
  ├── layout.tsx
  ├── globals.css
  ├── signup/ (회원가입)
  ├── logincallback/ (로그인 콜백)
  ├── search/ (검색)
  ├── product/
  │ ├── new/ (상품 등록)
  │ └── [id]/
  │ ├── page.tsx (상품 상세)
  │ └── edit/ (상품 수정)
  ├── shop/
  │ └── [id]/ (상점 페이지)
  ├── chat/
  │ ├── page.tsx (채팅 목록)
  │ ├── [roomId]/ (채팅방)
  │ └── payment/ (채팅 결제)
  ├── mypage/
  │ ├── page.tsx (마이페이지)
  │ ├── address/ (주소 관리)
  │ ├── purchases/ (구매 내역)
  │ ├── sales/ (판매 내역)
  │ ├── schedule/ (일정 관리)
  │ ├── settings/ (설정)
  │ ├── wishlist/ (찜 목록)
  │ └── withdrawal/ (회원탈퇴)
  ├── cs-center/ (고객센터)
  ├── admin/
  │ ├── page.tsx (관리자 메인)
  │ ├── inquiries/ (문의 관리)
  │ └── reports/ (신고 관리)
  ├── api/
  │ └── payment/
  │ └── confirm/ (결제 확인)
  └── test/
</details>

### Store 구조 (Zustand)
```
stores/
├── auth/
│   └── authStore.ts (로그인/로그아웃, 사용자 인증 상태)
├── chatting/
│   ├── chatRoomStore.ts (채팅방 관리, 메시지 처리)
│   ├── reservationStore.ts (예약 관리)
│   └── sendTypeMessage.ts (메시지 전송 타입 관리)
├── product/
│   ├── productStore.ts (상품 CRUD, 상품 목록 관리)
│   └── likeProductStore.ts (찜 기능, 좋아요 상태 관리)
├── mypage/
│   ├── myActivityStore.ts (사용자 활동 내역 - 구매/판매/리뷰)
│   ├── mySettingStore.ts (사용자 설정 관리)
│   ├── myAddressStore.ts (주소 관리)
│   └── myStore.ts (내 상점 관리)
├── admin/
│   ├── reportStore.ts (신고 관리)
│   └── inquiriesStore.ts (문의 관리)
├── cs-store/
│   ├── reportStore.ts (신고 기능)
│   └── inquiryStore.ts (문의 기능)
├── ai/
│   └── aiDescriptionStore.ts (AI 상품 설명 생성)
├── shop/
│   └── shopStore.ts (상점 정보 관리)
├── user/
│   └── userStore.ts (사용자 정보 관리)
├── modalStore.ts (모달 상태 관리)
├── loadingStore.ts (로딩 상태 관리)
├── notificationStore.ts (알림 관리)
├── signUpStore.ts (회원가입 프로세스)
├── chatBotStore.ts (챗봇 상태 관리)
├── imageUploadStore.ts (이미지 업로드 관리)
└── categoryStore.ts (카테고리 관리)
```

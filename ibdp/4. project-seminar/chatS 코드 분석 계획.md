

## 🎯 **ChatS 프로젝트 인수인계 코드 분석 로드맵**

---

## 📅 **Phase 1: 전체 시스템 아키텍처 파악 (우선순위 ⭐⭐⭐)**

### **🚀 가장 먼저 봐야 할 핵심 파일들**
Read file: start.sh
Read file: backend/VetServer.py
Read file: frontend/src/App.js
Read file: frontend/src/index.js

### **✅ Phase 1 완료 - 시스템 구조 파악**
Ran tool

## 📅 **Phase 2: 핵심 데이터 흐름 이해**

### **🔗 데이터 흐름의 핵심 컴포넌트들**
Read file: backend/Init_database.py
Read file: backend/Init_retriever.py
Read file: backend/Init_llm.py
Read file: frontend/src/MainPage/ui/JournalData.js

### **✅ Phase 2 완료 - 데이터 흐름 이해**
Ran tool

## 📅 **Phase 3: 백엔드 핵심 로직 분석**

### **🎯 주요 API 엔드포인트 및 비즈니스 로직**
Ran tool
Read file: backend/VetServer.py
Read file: backend/rerank_model.py
Read file: backend/Language_detect.py

### **✅ Phase 3 완료 - 백엔드 핵심 로직 분석**
Ran tool

## 📅 **Phase 4: 프론트엔드 구조 분석**

### **🎨 주요 페이지 및 컴포넌트 구조**
Read file: frontend/src/MainPage/MainPage.js
Read file: frontend/src/search_result/search_result.js
Read file: frontend/src/chatbot/chatbotPage.js
Read file: frontend/src/utils/apiClient.js

### **✅ Phase 4 완료 - 프론트엔드 구조 분석**
Ran tool

## 📅 **Phase 5: 데이터 파이프라인 이해**

### **🔄 데이터 처리 파이프라인의 전체 흐름**
Read file: sync_manager.py
Read file: PreProcess/embed/UpStage_embed.py
Read file: PostProcess/auto_crawler/1.Crosserf/recent_process/additional_recent.py
Read file: PostProcess/pdf_downloader/run_all_scripts.sh

### **✅ Phase 5 완료 - 데이터 파이프라인 이해**
Ran tool

## 📅 **Phase 6: 설정 및 환경 파악**

### **⚙️ 환경 설정 및 중요한 설정 파일들**
Ran tool
Ran tool
Read file: frontend/src/setupProxy.js
Ran tool

Ran tool
Ran tool
Ran tool
Read file: CLAUDE.md

### **✅ Phase 6 완료 - 설정 및 환경 파악**
Ran tool

---

# 🎯 **ChatS 프로젝트 인수인계 완전 가이드**

프로젝트 인수인계를 위한 **체계적인 6단계 로드맵**을 제공합니다. 각 단계는 복잡성과 중요도에 따라 설계되었습니다.

---

## 📋 **전체 로드맵 요약**

| **단계** | **목표** | **소요시간** | **난이도** |
|---------|----------|------------|----------|
| **Phase 1** | 시스템 전체 구조 파악 | 1-2시간 | ⭐⭐ |
| **Phase 2** | 핵심 데이터 흐름 이해 | 2-3시간 | ⭐⭐⭐ |
| **Phase 3** | 백엔드 핵심 로직 분석 | 3-4시간 | ⭐⭐⭐⭐ |
| **Phase 4** | 프론트엔드 구조 분석 | 2-3시간 | ⭐⭐⭐ |
| **Phase 5** | 데이터 파이프라인 이해 | 3-4시간 | ⭐⭐⭐⭐⭐ |
| **Phase 6** | 설정 및 환경 파악 | 1시간 | ⭐⭐ |

---

## 🚀 **Phase 1: 시스템 전체 구조 파악 (우선순위 최고)**

### **🎯 목표: 프로젝트 전체 그림 이해**

#### **필수 파일 순서**
1. **`README.md`** - 프로젝트 개요 및 기술 스택
2. **`start.sh`** - 시스템 실행 방법 (Flask + React)
3. **`frontend/src/index.js`** - 전체 라우팅 구조
4. **`backend/VetServer.py`** (1-100줄) - 주요 API 엔드포인트
5. **`frontend/src/App.js`** - 프론트엔드 진입점

#### **핵심 이해사항**
- **21개 수의학 저널** 통합 검색 플랫폼
- **Flask(5000) + React(3001)** 구조
- **하이브리드 검색** (벡터 + BM25)
- **3가지 챗봇 모드** (Simple/Inner/Deep)
- **실시간 번역** 및 **PDF 뷰어**

---

## 🔗 **Phase 2: 핵심 데이터 흐름 이해**

### **🎯 목표: 데이터가 어떻게 흘러가는지 파악**

#### **필수 파일 순서**
1. **`backend/Init_database.py`** - DB 연결 구조
2. **`backend/Init_retriever.py`** (1-100줄) - 검색 시스템 핵심
3. **`backend/Init_llm.py`** (1-100줄) - LLM 체인 구조
4. **`frontend/src/MainPage/ui/JournalData.js`** - 저널 데이터 구조

#### **핵심 이해사항**
- **MySQL**: 논문 메타데이터 저장
- **FAISS**: 벡터 검색 (UpStage 임베딩)
- **BM25**: 키워드 검색 (KiwiBM25Retriever)
- **Gemini 2.5**: 메인 LLM (OpenAI에서 전환)
- **21개 저널**: wiley/crossref/custom/subscribe 카테고리

---

## ⚙️ **Phase 3: 백엔드 핵심 로직 분석**

### **🎯 목표: API와 비즈니스 로직 이해**

#### **주요 API 엔드포인트**
```python
# 검색 관련
POST /search                    # 하이브리드 검색
POST /search_author            # 저자 검색
GET /recent_papers             # 최신 논문

# 챗봇 관련  
POST /chatbot_inference_streaming  # 스트리밍 응답
POST /chatbot_simple_response      # 단순 모드
POST /chatbot_query               # 이북 RAG

# 기타
POST /api/summation              # 보고서 생성
POST /pplx                       # Perplexity 연동
```

#### **필수 파일 순서**
1. **`backend/VetServer.py`** (400-500줄) - 주요 API 로직
2. **`backend/rerank_model.py`** - 리랭킹 시스템
3. **`backend/Language_detect.py`** - 언어 감지

#### **핵심 이해사항**
- **FlagReranker**: BAAI/bge-reranker-v2-m3 모델
- **Multi-Query**: 검색 정확도 향상
- **스트리밍 응답**: Server-Sent Events
- **언어 감지**: 한국어/영어 자동 처리

---

## 🎨 **Phase 4: 프론트엔드 구조 분석**

### **🎯 목표: React 컴포넌트 구조와 상태 관리 이해**

#### **페이지별 구조**
```
src/
├── MainPage/           # 저널 선택, 논문 리스트
├── search_result/      # 고급 검색, 필터링
├── chatbot/           # 다중 챗봇 (1148줄)
├── pdf_viewer/        # PDF + 번역
├── write_report/      # 월간 리포트
└── login/             # JWT 인증
```

#### **필수 파일 순서**
1. **`frontend/src/MainPage/MainPage.js`** (150-250줄) - 상태 관리
2. **`frontend/src/search_result/search_result.js`** (1-100줄) - 검색 UI
3. **`frontend/src/chatbot/chatbotPage.js`** (1-100줄) - 챗봇 UI
4. **`frontend/src/utils/apiClient.js`** - API 클라이언트 설정

#### **핵심 이해사항**
- **GlobalContext**: 전역 상태 관리
- **관심사 분리**: UI/API/Handler 분리
- **JWT 인증**: Authorization 헤더 자동 추가
- **반응형 디자인**: 모바일 최적화

---

## 🔄 **Phase 5: 데이터 파이프라인 이해**

### **🎯 목표: 크롤링부터 검색까지 전체 파이프라인 파악**

#### **데이터 처리 흐름**
```
논문 수집 → PDF 다운로드 → 임베딩 생성 → 벡터DB 저장 → 검색 서비스
```

#### **필수 파일 순서**
1. **`sync_manager.py`** (100-200줄) - 동기화 시스템 핵심
2. **`PreProcess/embed/UpStage_embed.py`** - 임베딩 생성
3. **`PostProcess/auto_crawler/1.Crosserf/recent_process/additional_recent.py`** - 자동 크롤링
4. **`PostProcess/pdf_downloader/run_all_scripts.sh`** - PDF 다운로더

#### **핵심 이해사항**
- **3가지 크롤러**: CrossRef/Wiley/Custom
- **Chrome 버전**: 131-133 (undetected_chromedriver)
- **UpStage 임베딩**: solar-embedding-1-large
- **동기화**: PDF 상태 + 벡터 DB 동기화

---

## ⚙️ **Phase 6: 설정 및 환경 파악**

### **🎯 목표: 환경 설정과 배포 방법 이해**

#### **환경 변수**
```bash
# 백엔드 (.env)
DATABASE_HOST=25.6.62.217
DATABASE_USER=root
DATABASE_PASSWORD=*****
DATABASE_NAME=chats_v1_main
GOOGLE_API_KEY=*****
UPSTAGE_API_KEY=*****
```

#### **필수 파일 순서**
1. **`CLAUDE.md`** - 개발 가이드 (230줄)
2. **`frontend/src/setupProxy.js`** - 프록시 설정
3. **`backend/Init_database.py`** - 환경변수 로딩

#### **핵심 이해사항**
- **프록시 설정**: localhost:5000 ↔ localhost:3001
- **JWT 인증**: localStorage 기반
- **API 타임아웃**: 300초 (대용량 처리)

---

## 🎯 **인수인계 후 첫 작업 추천**

### **1주차: 환경 구축 및 기본 이해**
```bash
# 1. 시스템 실행
./start.sh

# 2. 테스트 검색
curl "http://localhost:5000/search?QUERY=심장병&k=10"

# 3. 챗봇 테스트
# 브라우저에서 http://localhost:3001/chatS 접속
```

### **2주차: 코드 수정 실습**
- 새로운 저널 추가 시도
- 프롬프트 수정 (`backend/prompts/`)
- UI 컴포넌트 수정

### **3주차: 데이터 파이프라인 이해**
- PDF 다운로더 실행
- 임베딩 생성 과정 관찰
- 동기화 시스템 테스트

---

## 🚨 **주의사항**

### **개발 시 필수 확인사항**
1. **JWT 토큰**: API 호출 시 Authorization 헤더 필수
2. **CORS**: Flask-CORS 설정 확인
3. **스트리밍**: AbortController로 요청 관리
4. **동기화**: 데이터 변경 후 반드시 sync_manager.py 실행

### **문제 해결**
- **백엔드 오류**: `backend/backend.log` 확인
- **프론트엔드 오류**: 브라우저 개발자 도구 Console
- **DB 연결**: MySQL 서버 상태 확인
- **GPU 메모리**: CUDA 장치 상태 확인

# 📄📢 AI-NutriCurator

만성질환 중증도 환자들은 일상적인 커머스 환경에서도 본인의 건강 상태에 적합한 식품을 선택하는 데 정보의 비대칭성 및 상품 탐색 과정에서의 불편함을 겪고 있습니다. 
본 AI서비스는 신뢰도 높은 출처 기반으로 구축된 DB를 바탕으로 정확도 높은 메세지 생성 및 추천 로직을 통해 이를 해소하고자 합니다.

## Team BuildSparkDevelopers

팀장: 소형선 이영주 박수빈

## 🚀 주요 기능

- **사용자 프로필 관리**: 알러지 정보 및 건강 제한사항 관리
- **제품 알러지 분석**: 22종 식약처 고시 알레르기 유발 물질 기준 분석
- **대체재 추천**: 알러지 성분에 대한 안전한 대체 식재료 추천
- **실시간 검색**: 제품명 및 원재료 기반 검색 기능
- **안전성 평가**: 제품 섭취 가능 여부 및 위험도 평가

## 📦 프로젝트 구조

```
AI-NutriCurator/
├── backend/
│   └── app.py              # FastAPI 백엔드 서버
├── index.html              # 프론트엔드 웹 인터페이스
├── requirements.txt        # Python 의존성
├── package.json           # Node.js 의존성 (선택사항)
└── agent_chat_allergy(완).py  # AI 모델 통합 스크립트
```

## 🛠️ 설치 및 실행

### 1. Python 환경 설정

```bash
# Python 가상환경 생성 (선택사항)
python -m venv venv

# Windows
venv\Scripts\activate

# Mac/Linux
source venv/bin/activate

# 의존성 설치
pip install -r requirements.txt
```

### 2. 백엔드 서버 실행

```bash
cd backend
python app.py
```

또는 uvicorn 직접 실행:

```bash
uvicorn backend.app:app --reload --host 0.0.0.0 --port 8000
```

서버가 `http://localhost:8000`에서 실행됩니다.

### 3. 프론트엔드 실행

프론트엔드는 정적 HTML 파일이므로 다음 방법 중 하나로 실행할 수 있습니다:

**방법 1: 라이브 서버 (VSCode 확장)**
- VSCode에서 `index.html` 파일을 열고 "Go Live" 클릭

**방법 2: Python 간단 서버**
```bash
python -m http.server 3000
```

**방법 3: 브라우저에서 직접 열기**
```bash
# index.html 파일을 브라우저로 드래그 앤 드롭
```

프론트엔드는 `http://localhost:3000` 또는 직접 열어서 접근합니다.

## 📡 API 엔드포인트

### 제품 관련
- `GET /products` - 전체 제품 목록 조회
- `GET /products/{product_id}` - 특정 제품 상세 조회
- `GET /search?q={query}` - 제품 검색

### 프로필 관련
- `GET /profiles` - 사용자 프로필 목록 조회
- `GET /profiles/{profile_id}` - 특정 프로필 조회

### 분석
- `POST /analyze` - 제품 알러지 분석
  ```json
  {
    "product_id": "0",
    "profile_id": "0"
  }
  ```

## 🎨 사용 방법

1. **프로필 선택**: 상단에서 자신의 건강 상태에 맞는 프로필을 선택합니다.
2. **제품 검색**: 검색창에 제품명이나 원재료를 입력하여 제품을 찾습니다.
3. **알러지 분석**: 제품 카드의 "알러지 분석" 버튼을 클릭합니다.
4. **결과 확인**: 
   - ✅ **안전**: 알러지 성분이 검출되지 않음
   - ⚠️ **주의**: 교차오염 가능성 있음
   - ❌ **위험**: 알러지 성분 포함, 섭취 금지

## 🔧 기술 스택

### 백엔드
- **FastAPI**: 고성능 Python 웹 프레임워크
- **Pydantic**: 데이터 검증
- **Uvicorn**: ASGI 서버

### 프론트엔드
- **HTML5 / CSS3 / JavaScript (Vanilla)**
- **Tailwind CSS**: 스타일링
- **Font Awesome**: 아이콘

### AI/ML (선택사항)
- **PyTorch**: 딥러닝 프레임워크
- **Transformers**: 사전 학습 모델 (Qwen2.5)

## 📊 데이터베이스

현재는 인메모리 데이터를 사용하고 있습니다. 프로덕션 환경에서는 다음을 고려하세요:

- PostgreSQL / MySQL
- MongoDB (문서 기반)
- SQLite (개발/테스트)

## 🔐 보안 고려사항

- API 인증/인가 구현 필요
- HTTPS 사용 권장
- 입력 데이터 검증
- SQL Injection 방지
- XSS 공격 방지

## 🚧 향후 개발 계획

- [ ] 사용자 계정 및 인증 시스템
- [ ] 데이터베이스 통합
- [ ] 실제 AI 모델 통합 (Qwen2.5)
- [ ] 제품 바코드 스캔 기능
- [ ] 영양 성분 분석
- [ ] 개인화된 식단 추천
- [ ] 모바일 앱 개발

## 📝 라이센스

MIT License

## 👥 기여자

- 소형선 (팀장)
- 이영주
- 박수빈

## 📞 문의

프로젝트에 대한 문의사항이 있으시면 이슈를 등록해주세요.

---

**⚠️ 면책 조항**: 이 시스템은 보조 도구이며, 실제 의료 조언을 대체할 수 없습니다. 심각한 알러지가 있는 경우 반드시 전문의와 상담하세요.

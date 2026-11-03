# 🩺 메디케어 AI

증상, 식습관, 생활 습관을 입력하면 AI가 **가능한 원인과 일반적인 건강 관리 정보**를 알려주는 Streamlit 데모입니다. **확진·진료·처방을 대신하지 않습니다.**

## 파일
- `app.py`: Streamlit 웹사이트
- `requirements.txt`: 필요한 패키지
- `.streamlit/secrets.toml.example`: 로컬 비밀키 설정 예시
- `.gitignore`: 비밀키 및 불필요 파일 공개 방지

## GitHub + Streamlit Community Cloud 배포
1. GitHub에서 새 저장소(예: `medicare-ai`)를 만듭니다.
2. 이 폴더의 `app.py`, `requirements.txt`, `.gitignore`, `README.md`를 저장소에 업로드합니다. 예시 키 파일은 업로드해도 되지만, **실제 키가 들어간 `.streamlit/secrets.toml`은 절대 업로드하지 마세요.**
3. https://share.streamlit.io 에 로그인하고 **Create app → GitHub 저장소 선택**을 클릭합니다.
4. **Main file path**에 `app.py`를 설정합니다.
5. **Advanced settings → Secrets**에 아래 내용을 넣습니다(실제 키로 변경).
   ```toml
   OPENAI_API_KEY = "sk-..."
   ```
6. Deploy를 클릭합니다.

## 로컬 실행
Python 3.10 이상을 권장합니다.

```bash
pip install -r requirements.txt
mkdir -p .streamlit
# .streamlit/secrets.toml.example을 .streamlit/secrets.toml로 복사하고 실제 키를 입력
streamlit run app.py
```

## 안전·운영 유의사항
- 응급 증상 선택 시 AI 요청 없이 즉시 119 안내를 표시합니다. 자유 입력 문장에 있는 위험 징후는 AI도 판별하도록 요청하지만 **규칙 기반 선별을 완벽하게 대체하지 못합니다**.
- AI 결과는 구조화된 형식으로 받지만, 의학적 정확성은 보장되지 않습니다.
- 앱 코드에서 건강정보를 파일이나 DB에 저장하지 않지만, 외부 AI API로 전송됩니다. 실제 공개 서비스라면 개인정보 보호 관련 고지·동의·처리방침, 데이터 보관 및 삭제, 접근 통제, 로그 관리, 임상 검수 및 관련 법률 검토가 필요합니다.
- 사용량에 따라 OpenAI API 과금이 발생합니다. Streamlit 호스팅과 API 요금은 별개입니다.
- 실제 운영 전 임상의 자문, 안전성 테스트, 오남용 방지, 비정상 요청 차단 및 비용 한도 설정이 필요합니다.

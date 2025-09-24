# Hangeul HWP/HWPX → PDF API

국내 문서 포맷 **HWP/HWPX** 파일을 고품질 **PDF**로 변환하는 API & SDK 예제 리포지토리입니다.  
Rapid에서 즉시 호출하거나, 서버 프록시/온프렘으로 확장할 수 있습니다.

[![Rapid – Hangeul → PDF](https://img.shields.io/badge/RapidAPI-Hangeul%20Converter-2E8B57)](#)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Issues](https://img.shields.io/github/issues/OWNER/hwp-hwpx-to-pdf-api)](../../issues)
[![Stars](https://img.shields.io/github/stars/OWNER/hwp-hwpx-to-pdf-api)](../../stargazers)

---

## ✨ 기능
- 입력: `fileUrl`, `fileName`
- 출력: 변환된 PDF 서명 URL (`file`)
- 응답 포맷(성공/실패 동일 200 반환):
```json
{
  "success": true,
  "message": "",
  "file": "https://storage.googleapis.com/.../sample.pdf"
}
```
- 한글 폰트 대체 규칙 → 레이아웃 깨짐 최소화  
- 임시 저장 후 자동 삭제(보안 모드)

---

## 🚀 빠른 시작

### 1) Rapid에서 호출
```bash
curl -G 'https://hangeul-hwp-hwpx-pdf-byeonhwan-api.p.rapidapi.com/convertHwpToPdf'   --data-urlencode 'fileUrl=https://example.com/sample.hwp'   --data-urlencode 'fileName=sample.hwp'   -H 'X-RapidAPI-Host: <api-name>.p.rapidapi.com'   -H 'X-RapidAPI-Key: <YOUR_KEY>'
```

#### JavaScript (axios)
```js
import axios from "axios";
const { data } = await axios.get("https://hangeul-hwp-hwpx-pdf-byeonhwan-api.p.rapidapi.com/convertHwpToPdf", {
  params: { fileUrl: "https://example.com/sample.hwp", fileName: "sample.hwp" },
  headers: { "X-RapidAPI-Host": "<api-name>.p.rapidapi.com", "X-RapidAPI-Key": process.env.RAPID_KEY }
});
console.log(data.file); // PDF URL
```

#### Python (requests)
```python
import requests
r = requests.get(
  "https://hangeul-hwp-hwpx-pdf-byeonhwan-api.p.rapidapi.com/convertHwpToPdf",
  params={"fileUrl":"https://example.com/sample.hwp","fileName":"sample.hwp"},
  headers={"X-RapidAPI-Host":"<api-name>.p.rapidapi.com","X-RapidAPI-Key":"<YOUR_KEY>"}
)
print(r.json()["file"])
```

> ⚠️ Rapid 콘솔/클라이언트가 키를 자동 주입하면 `X-RapidAPI-Key`를 코드에 넣지 않아도 됩니다.

---

## 📦 OpenAPI
`/openapi/openapi.yaml`에 엔드포인트 정의가 포함됩니다.  
- `POST /convertHwpToPdf ` (또는 `GET /convertHwpToPdf` params)  
- 요청: `fileUrl`, `fileName`  
- 응답: `success`, `message`, `file`

---

## 🔐 보안/프라이버시
- 업로드 파일은 임시 저장 후 자동 삭제됩니다.
- 본 프로젝트는 데이터 보관 책임을 지지 않습니다. 합법적인 용도에 한해 사용하세요.

---

## 💳 가격/플랜 (요약)
- Free: 1건/일  
- Starter: **$15 → 700건**  
- Pro: **$30 → 1500건**  
- Pay as you go: **$0.1/per**  
- Enterprise/온프렘: 문의

자세한 내용은 Rapid 페이지 요금 섹션 참고.

---

## ❓FAQ
**Q. PDF가 브라우저에서 바로 열리나요?**  
A. 네, `Content-Type: application/pdf` 또는 `.pdf` 확장자면 브라우저 내장 뷰어로 바로 열립니다.  
`Content-Disposition: inline`이면 인라인, `attachment`면 다운로드가 뜹니다.

**Q. 멀티파트 업로드도 되나요?**  
A. 권장은 `fileUrl` 전달 방식입니다(서명 URL). 멀티파트는 프록시 서버에서 처리 바랍니다.

---

## 🛠 로컬 개발(선택)
```bash
pnpm i
pnpm dev
# .env에 RAPID_KEY, STORAGE_BUCKET 등 환경변수 설정
```

---

## 🤝 기여
이슈/PR 환영합니다. 가이드: `CONTRIBUTING.md`  
보안 제보: `SECURITY.md`

---

## 📄 라이선스
MIT

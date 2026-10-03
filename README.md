# Lumen Reader - Ultimate Final

아름다운 서재 디자인 그대로 + 오프라인 + CP949 자동 복구.

## 포함 파일
- index.html : 싱글 파일 PWA 리더 (Fraunces, Noto Serif KR, paper #FFFEFB, glass header 64px, ornament •—•, drop-cap, bottom island #1A1A18, TOC 380px dotted leader)
- manifest.json : PWA 매니페스트
- sw.js : 오프라인 캐시 (CACHE lumen-ultimate-v2)
- icon-192.png / icon-512.png : 검정 라운드 + 골드 라인 + L
- README.md

## GitHub Pages 교체 방법
1. 이 ZIP을 해제합니다.
2. 기존 GitHub Pages 리포지토리 루트에 파일 5개를 덮어씌웁니다.
   - index.html (기존 파일 교체)
   - manifest.json
   - sw.js
   - icon-192.png
   - icon-512.png
3. git add . / git commit -m "chore: lumen ultimate final 교체" / git push
4. Pages 배포 후 강력 새로고침. 오프라인 확인은 비행기 모드에서 재접속.

## 기능 요약
- 단일 전역 파일 입력 #global-file (left -9999px) + window.openFilePicker 직접 click
- 터치/클릭 모두 onTouchEnd + onClick 직접 호출, preventDefault 처리 없음
- CP949 → EUC-KR → UTF-8 3단계 디코딩, 0x81-0xFE 휴리스틱
- decodeEntities, isDialogue, isStrictHeading, Set 기반 중복 제거
- hybrid TOC 3-stage ( -1- / ● ● / 일반 제목 )
- html/body overflow auto, body.toc-open hidden, localStorage recent/progress/bookmark
- PWA manifest data URI + sw blob fallback + 실파일 등록

# 🛒 쇼핑 리스트

Supabase 데이터베이스와 연동된 간단한 쇼핑 리스트 웹 앱입니다. 별도 빌드 과정 없이 `index.html` 파일을 브라우저로 열기만 하면 바로 사용할 수 있습니다.

## 기능

- 물건 추가 / 삭제
- 항목 체크(완료 처리)
- 완료된 항목 일괄 삭제
- 전체/완료 개수 표시
- Supabase(`shopping_items` 테이블)에 데이터 저장 (기기/브라우저와 무관하게 유지)

## 실행 방법

`index.html` 파일을 브라우저에서 열면 됩니다. 별도의 설치나 서버가 필요 없습니다.

## 데이터베이스

Supabase 프로젝트에 다음 테이블을 사용합니다.

```sql
create table public.shopping_items (
  id bigint generated always as identity primary key,
  text text not null,
  done boolean not null default false,
  created_at timestamptz not null default now()
);
```

클라이언트는 `index.html`에 포함된 Supabase 프로젝트 URL과 공개 가능한(publishable) anon 키를 사용해 직접 데이터베이스에 접근합니다. 이 앱은 별도의 로그인 기능이 없는 단일 사용자용 앱이므로, RLS 정책이 `anon` 역할에 대해 읽기/쓰기를 모두 허용하도록 설정되어 있습니다.

[![적용기술](https://skillicons.dev/icons?i=nextjs,ts,react)](https://skillicons.dev)

### INDEX
1. 개요
2. 라우팅
3. 라우팅 패턴
4. 인증
5. 서버 액션
6. 최적화
7. 배포

---

# 개요

### 
<p>다음은 Next.js 15의 주요 업데이트 내용입니다.</p>
<ul>
    <li><strong>자동화된 업그레이드 CLI(<code>@next/codemod</code>)</strong><ul>
    <li>Next.js 버전을 쉽게 업그레이드할 수 있는 CLI가 제공됩니다. </li><li><code>npx @next/codemod@canary upgrade latest</code> 명령어로 업그레이드할 수 있습니다.</li><li>상세한 코드 변경까지는 변경이 되지 않아서 추가 확인 작업이 필요합니다.</li></ul>
    </li><li><strong>비동기 요청 API (중요)</strong><ul>
    <li>데이터 요청이 필요 없는 컴포넌트를 비동기로 처리하여 초기 로드 속도를 높이는 방향으로 변경되었습니다.</li><li><code>params</code>나 <code>searchParams</code> 등의 주요 API가 비동기 사용으로 전환되었습니다.</li></ul>
    </li><li><strong>캐싱 기본값 변경 (중요)</strong><ul>
    <li>GET 요청 및 클라이언트 내비게이션의 기본 캐싱 설정이 해제되었습니다.</li><li>TanStack Query 같은 라이브러리의 캐싱 기능과 중복되지 않아서 좋습니다.</li><li><code>cache: 'force-cache'</code> 옵션으로 다시 캐싱할 수 있습니다.</li></ul>
    </li><li><strong>React 19 지원 (중요)</strong><ul>
    <li>React 19와의 호환성을 지원하며, React 18과도 일부 하위 호환이 유지됩니다.</li></ul>
    </li><li><strong><code>&lt;Form&gt;</code> 컴포넌트</strong><ul>
    <li><code>&lt;form&gt;</code> 요소를 확장한 최적화 컴포넌트로, 제출 경로를 프리패칭(Prefetching)하고 제출 데이터를 쿼리스트링으로 보존합니다.</li></ul>
    </li><li><strong>Turbopack Dev 안정화</strong><ul>
    <li><code>next dev --turbo</code> 모드가 안정화되어, 더 빠른 개발 환경과 반응 속도를 제공합니다.</li></ul>
    </li><li><strong>정적 라우트 표시기</strong><ul>
    <li>개발 중에 경로가 사전 렌더링되는지 여부를 화면 하단 모서리에 표시(⚡ Static route)합니다.</li></ul>
    </li><li><strong>비동기 처리 후 코드 실행 API</strong> (<code>unstable_after</code>)<ul>
    <li>스트리밍이 완료된 후 비동기적으로 추가 작업을 처리할 수 있는 새로운 API입니다.</li><li>아직 안정화 전이니 참고만 하는 것이 좋겠습니다.</li></ul>
    </li><li><strong><code>/instrumentation.js</code> API 안정화</strong><ul>
    <li>서버 생명주기를 관찰하여 성능을 모니터링하고 오류를 추적할 수 있습니다.</li></ul>
    </li><li><strong>TypeScript 구성 지원</strong><ul>
    <li>TypeScript를 사용하는 설정 파일을 지원하며 자동 완성과 타입 안전성도 보장됩니다.</li></ul>
    </li><li><strong>자체 호스팅 개선</strong><ul>
    <li>캐시 제어 헤더에 대한 더 많은 제어와 이미지 최적화 성능이 향상되었습니다.</li></ul>
    </li><li><strong>보안 강화</strong><ul>
    <li>서버 액션이 공개 엔드포인트가 되는 것을 방지하기 위한 기능이 추가되어 보안이 강화되었습니다.</li></ul>
    </li><li><strong>외부 패키지 번들링 최적화</strong><ul>
    <li>외부 패키지를 번들링할 수 있는 설정 옵션이 추가되었습니다.</li></ul>
    </li><li><strong>ESLint 9 지원</strong><ul>
    <li>ESLint 9를 지원하여 최신 규칙을 반영하고 호환성을 유지합니다.</li></ul>
    </li><li><strong>빌드 및 개발 성능 개선</strong><ul>
    <li>정적 페이지 생성 최적화와 서버 컴포넌트의 HMR 기능이 강화되었습니다.</li></ul>
    </li>
</ul>

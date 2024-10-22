---
id: release_notes.md
summary: Milvus 릴리스 노트
title: 릴리스 노트
---
<h1 id="Release-Notes" class="common-anchor-header">릴리스 노트<button data-href="#Release-Notes" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h1><p>Milvus의 새로운 기능을 알아보세요! 이 페이지에는 각 릴리스의 새로운 기능, 개선 사항, 알려진 문제 및 버그 수정 사항이 요약되어 있습니다. 이 섹션에서 v2.4.0 이후 출시된 각 버전에 대한 릴리스 노트를 확인할 수 있습니다. 이 페이지를 정기적으로 방문하여 업데이트에 대해 알아보는 것이 좋습니다.</p>
<h2 id="v2413-hotfix" class="common-anchor-header">v2.4.13-핫픽스<button data-href="#v2413-hotfix" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜: 2024년 10월 17일</p>
<table>
<thead>
<tr><th>Milvus 버전</th><th>Python SDK 버전</th><th>Java SDK 버전</th><th>Node.js SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.13 핫픽스</td><td>2.4.8</td><td>2.4.5</td><td>2.4.9</td></tr>
</tbody>
</table>
<p>Milvus v2.4.13-hotfix는 모든 MetaKV 스냅샷이 가비지 수집된 경우 재시작 후 수집 정보를 검색하지 못할 수 있는 v2.4.13과 관련된 중요한 문제를 해결합니다<a href="https://github.com/milvus-io/milvus/pull/36933">(#36933</a>). <strong>현재 v2.4.13을 실행 중인 사용자는 잠재적인 중단을 피하기 위해 가능한 한 빨리 v2.4.13 핫픽스로 업그레이드하는 것이 좋습니다</strong>.</p>
<h3 id="Critical-fixes" class="common-anchor-header">중요 수정 사항</h3><ul>
<li>타임스탬프가 MaxTimestamp인 경우 원본 키 로드<a href="https://github.com/milvus-io/milvus/pull/36935">(#36935</a>)</li>
</ul>
<h2 id="Deprecated-v2413" class="common-anchor-header">[사용 중단됨] v2.4.13<button data-href="#Deprecated-v2413" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜: 2024년 10월 12일</p>
<table>
<thead>
<tr><th>Milvus 버전</th><th>Python SDK 버전</th><th>Java SDK 버전</th><th>Node.js SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.13</td><td>2.4.8</td><td>2.4.5</td><td>2.4.9</td></tr>
</tbody>
</table>
<p>Milvus 2.4.13은 동적 복제본 로드를 도입하여 사용자가 컬렉션을 해제하고 다시 로드할 필요 없이 컬렉션 복제본의 수를 조정할 수 있도록 합니다. 이 버전은 또한 대량 가져오기, 표현식 구문 분석, 로드 밸런싱 및 장애 복구와 관련된 몇 가지 중요한 버그를 해결합니다. 또한 MMAP 리소스 사용량과 가져오기 성능이 크게 개선되어 전반적인 시스템 효율성이 향상되었습니다. 더 나은 성능과 안정성을 위해 이 릴리스로 업그레이드하는 것을 적극 권장합니다.</p>
<h3 id="Features" class="common-anchor-header">주요 기능</h3><ul>
<li>로드된 컬렉션에 대한 동적 복제본 조정<a href="https://github.com/milvus-io/milvus/pull/36417">(#36417</a>)</li>
<li>증가하는 세그먼트 유형에서 스파스 벡터 MMAP<a href="https://github.com/milvus-io/milvus/pull/36565">(#36565</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">버그 수정</h3><ul>
<li>플러시 성능 문제 수정<a href="https://github.com/milvus-io/milvus/pull/36741">(#36741</a>)</li>
<li>&quot;[]&quot;의 JSON 표현식 관련 버그 수정<a href="https://github.com/milvus-io/milvus/pull/36722">(#36722</a>).</li>
<li>컴팩트 타겟이 인덱싱되지 않은 경우 이웃 제거<a href="https://github.com/milvus-io/milvus/pull/36694">(#36694</a>).</li>
<li>채널이 꽉 찼을 때 Rocksmq의 성능 개선<a href="https://github.com/milvus-io/milvus/pull/36618">(#36618</a>).</li>
<li>고정 해제 중 오류가 지연되지 않던 문제 수정<a href="https://github.com/milvus-io/milvus/pull/36665">(#36665</a>).</li>
<li>세그먼트 매니저에서 가져온 세그먼트의 메모리 누수 문제 해결<a href="https://github.com/milvus-io/milvus/pull/36631">(#36631</a>)</li>
<li>프록시에서 쿼리 노드에 대한 불필요한 상태 검사 생략<a href="https://github.com/milvus-io/milvus/pull/36553">(#36553</a>).</li>
<li>용어 표현식의 오버플로 문제 수정<a href="https://github.com/milvus-io/milvus/pull/36534">(#36534</a>)</li>
<li>작업 할당 전에 노드 ID를 기록하여 작업 오할당을 방지<a href="https://github.com/milvus-io/milvus/pull/36493">(#36493</a>).</li>
<li>클러스터링 압축 시 데이터 경합 문제 해결<a href="https://github.com/milvus-io/milvus/pull/36499">(#36499</a>)</li>
<li>유형 일치 후 문자열 배열 최대 길이 검사 추가<a href="https://github.com/milvus-io/milvus/pull/36497">(#36497</a>).</li>
<li>혼합 또는 독립 실행형 모드에서 경쟁 조건 해결<a href="https://github.com/milvus-io/milvus/pull/36459">(#36459</a>)</li>
<li>반복적인 로드 및 릴리스 작업 후 세그먼트 불균형 수정<a href="https://github.com/milvus-io/milvus/pull/36543">(#36543</a>).</li>
<li>중지 노드에서 세그먼트를 이동할 수 없는 코너 케이스 수정<a href="https://github.com/milvus-io/milvus/pull/36475">(#36475</a>).</li>
<li>일부 세그먼트가 누락된 경우에도 세그먼트 정보가 정상적으로 업데이트됨<a href="https://github.com/milvus-io/milvus/pull/36729">(#36729</a>).</li>
<li>etcd 트랜잭션이 스냅샷 KV의 최대 한도를 초과하지 않도록 수정<a href="https://github.com/milvus-io/milvus/pull/36773">(#36773</a>).</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">개선 사항</h3><ul>
<li>MMAP 리소스 추정 기능이 향상되었습니다:<ul>
<li>column.h의 MMAP 관련 코드 개선<a href="https://github.com/milvus-io/milvus/pull/36521">(#36521</a>)</li>
<li>컬렉션 로드 시 리소스 추정 개선<a href="https://github.com/milvus-io/milvus/pull/36728">(#36728</a>)</li>
</ul></li>
<li>성능 개선:<ul>
<li>유니코드를 ASCII로 변환하여 표현식 구문 분석 효율성 개선<a href="https://github.com/milvus-io/milvus/pull/36676">(#36676</a>)</li>
<li>여러 주제에 대한 메시지 병렬 생성 활성화<a href="https://github.com/milvus-io/milvus/pull/36462">(#36462</a>)</li>
<li>인덱스 파일 크기 계산 시 CPU 오버헤드 감소<a href="https://github.com/milvus-io/milvus/pull/36580">(#36580</a>)</li>
<li>헤더에서 메시지 유형을 검색하여 마샬링 해제 최소화<a href="https://github.com/milvus-io/milvus/pull/36454">(#36454</a>)</li>
<li>워크로드 기반 복제본 선택 정책 최적화<a href="https://github.com/milvus-io/milvus/pull/36384">(#36384</a>)</li>
</ul></li>
<li>최대 메시지 크기 제한에 맞게 삭제 작업 메시지 분할<a href="https://github.com/milvus-io/milvus/pull/36574">(#36574</a>)</li>
<li>가져오기 작업을 설명하는 새로운 RESTful URL 추가<a href="https://github.com/milvus-io/milvus/pull/36754">(#36754</a>).</li>
<li>가져오기 스케줄 최적화 및 시간 비용 메트릭 추가<a href="https://github.com/milvus-io/milvus/pull/36684">(#36684</a>)</li>
<li>쿼리 코디네이터 밸런서에 대한 잔액 보고서 로그 추가<a href="https://github.com/milvus-io/milvus/pull/36749">(#36749</a>).</li>
<li>공통 GC 구성 사용으로 전환<a href="https://github.com/milvus-io/milvus/pull/36670">(#36670</a>)</li>
<li>위임자에 대한 스트리밍 포워드 정책 스위치 추가<a href="https://github.com/milvus-io/milvus/pull/36712">(#36712</a>).</li>
<li>인덱스가 없는 컬렉션에 대한 수동 압축 활성화<a href="https://github.com/milvus-io/milvus/pull/36581">(#36581</a>)</li>
<li>다양한 메모리 용량을 가진 쿼리 노드에서 로드 밸런싱 활성화<a href="https://github.com/milvus-io/milvus/pull/36625">(#36625</a>).</li>
<li>metrics.label을 사용하는 인바운드 레이블의 통합 케이스<a href="https://github.com/milvus-io/milvus/pull/36616">(#36616</a>)</li>
<li>전송 채널/세그먼트 작업을 비활성화<a href="https://github.com/milvus-io/milvus/pull/36552">(#36552</a>).</li>
<li>가져오기 처리량 및 가져온 행 수를 모니터링하는 메트릭 추가<a href="https://github.com/milvus-io/milvus/pull/36588">(#36588</a>)</li>
<li>대상에 여러 타이머 객체가 생성되는 것을 방지<a href="https://github.com/milvus-io/milvus/pull/36573">(#36573</a>).</li>
<li>표현식 버전 업데이트 및 표현식에 대한 형식화된 HTTP 응답<a href="https://github.com/milvus-io/milvus/pull/36467">(#36467</a>)</li>
<li>스냅샷 KV에서 향상된 가비지 수집<a href="https://github.com/milvus-io/milvus/pull/36793">(#36793</a>)</li>
<li>컨텍스트 매개변수가 있는 메서드 실행 지원 추가<a href="https://github.com/milvus-io/milvus/pull/36798">(#36798</a>).</li>
</ul>
<h2 id="v2412" class="common-anchor-header">v2.4.12<button data-href="#v2412" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜: 2024년 9월 26일</p>
<table>
<thead>
<tr><th>Milvus 버전</th><th>Python SDK 버전</th><th>Java SDK 버전</th><th>Node.js SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.12</td><td>2.4.7</td><td>2.4.4</td><td>2.4.9</td></tr>
</tbody>
</table>
<p>Milvus 2.4.12는 중요한 버그 수정과 중요한 개선 사항을 도입했습니다. 이번 릴리스에서는 데이터 중복 문제를 해결하고 특히 대량의 삭제를 처리할 때 장애 복구 속도를 개선했습니다. 그러나 대량의 데이터를 삭제할 때 장애 복구 속도가 느려지는 알려진 문제가 여전히 남아 있습니다. 이 문제를 해결하기 위해 적극적으로 노력하고 있습니다.</p>
<h3 id="Improvements" class="common-anchor-header">개선 사항</h3><ul>
<li>플로우그래프 매니저에 대한 유예 중지 구현<a href="https://github.com/milvus-io/milvus/pull/36358">(#36358</a>)</li>
<li>로드되지 않은 벡터 필드에 대한 인덱스 검사 비활성화<a href="https://github.com/milvus-io/milvus/pull/36280">(#36280</a>)</li>
<li>델타 로드 중 히트되지 않은 삭제 레코드 필터링<a href="https://github.com/milvus-io/milvus/pull/36272">(#36272</a>)</li>
<li>std::stoi 예외에 대한 오류 처리 개선<a href="https://github.com/milvus-io/milvus/pull/36296">(#36296</a>)</li>
<li>필드 이름 또는 동적 필드 이름으로 허용되지 않는 키워드<a href="https://github.com/milvus-io/milvus/pull/36108">(#36108</a>)</li>
<li>L0 세그먼트에서 항목 삭제에 대한 메트릭 추가<a href="https://github.com/milvus-io/milvus/pull/36227">(#36227</a>)</li>
<li>원격 로딩을 지원하기 위해 L0 포워드 정책 구현<a href="https://github.com/milvus-io/milvus/pull/36208">(#36208</a>)</li>
<li>프록시에서 ANN 필드 로드 확인 추가<a href="https://github.com/milvus-io/milvus/pull/36194">(#36194</a>)</li>
<li>빈 스파스 행 지원 활성화<a href="https://github.com/milvus-io/milvus/pull/36061">(#36061</a>)</li>
<li>보안 취약점 수정<a href="https://github.com/milvus-io/milvus/pull/36156">(#36156</a>)</li>
<li>요청/응답 크기 메트릭에 대한 통계 핸들러 구현<a href="https://github.com/milvus-io/milvus/pull/36118">(#36118</a>)</li>
<li>인코딩된 배열 데이터의 크기 추정 수정<a href="https://github.com/milvus-io/milvus/pull/36379">(#36379</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">버그 수정</h3><ul>
<li>두 개의 벡터 필드가 있는 컬렉션의 메트릭 유형 오류 해결<a href="https://github.com/milvus-io/milvus/pull/36473">(#36473</a>)</li>
<li>메시지 큐 수신 실패를 유발하는 긴 버퍼링 문제 수정<a href="https://github.com/milvus-io/milvus/pull/36425">(#36425</a>)</li>
<li>분할 지원 후 적절한 압축-세그먼트 반환 구현<a href="https://github.com/milvus-io/milvus/pull/36429">(#36429</a>).</li>
<li>노드 ID 확인 고루틴의 데이터 경합 문제 해결<a href="https://github.com/milvus-io/milvus/pull/36377">(#36377</a>).</li>
<li>요소 유형 검사 제거<a href="https://github.com/milvus-io/milvus/pull/36324">(#36324</a>)</li>
<li>성장 및 봉인된 세그먼트의 동시 액세스 문제 수정<a href="https://github.com/milvus-io/milvus/pull/36288">(#36288</a>).</li>
<li>향후 스테이트풀 잠금 구현<a href="https://github.com/milvus-io/milvus/pull/36333">(#36333</a>)</li>
<li>하이브리드 검색에서 오프셋 사용 수정<a href="https://github.com/milvus-io/milvus/pull/36287">(#36287</a>, <a href="https://github.com/milvus-io/milvus/pull/36253">#36253</a>)</li>
<li>쿼리 노드에서 더티 세그먼트/채널 누수 해결<a href="https://github.com/milvus-io/milvus/pull/36259">(#36259</a>).</li>
<li>기본 키 중복 처리 수정<a href="https://github.com/milvus-io/milvus/pull/36274">(#36274</a>)</li>
<li>검색 요청에서 메트릭 유형 설정 강제 적용<a href="https://github.com/milvus-io/milvus/pull/36279">(#36279</a>)</li>
<li>저장된 인덱스 파일 크기 메트릭 지우기 문제 수정<a href="https://github.com/milvus-io/milvus/pull/36161">(#36161</a>)</li>
<li>글로벌 API 액세스에 대한 읽기 쓰기 권한 그룹 동작 수정<a href="https://github.com/milvus-io/milvus/pull/36145">(#36145</a>)</li>
</ul>
<h2 id="v2411" class="common-anchor-header">v2.4.11<button data-href="#v2411" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜 2024년 9월 11일</p>
<table>
<thead>
<tr><th>Milvus 버전</th><th>Python SDK 버전</th><th>Java SDK 버전</th><th>Node.js SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.11</td><td>2.4.6</td><td>2.4.3</td><td>2.4.8</td></tr>
</tbody>
</table>
<p>Milvus 2.4.11은 MARISA 트라이 인덱스, 압축 및 로딩 작업과 관련된 여러 가지 중요한 문제를 해결하는 버그 수정 릴리스입니다. 이 릴리스에는 표현식을 보고 삭제 안정성을 개선하는 새로운 기능이 도입되었습니다. 2.4.x 시리즈의 모든 사용자는 이 버전으로 업그레이드하여 이러한 개선 사항과 수정 사항을 활용하시기 바랍니다.</p>
<h3 id="Features" class="common-anchor-header">주요 기능</h3><ul>
<li>2.4에서 표현식에 대한 정적 보기 추가<a href="https://github.com/milvus-io/milvus/pull/35954">(#35954</a>)</li>
<li>버퍼 삭제 관련 할당량 로직 구현<a href="https://github.com/milvus-io/milvus/pull/35997">(#35997</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">버그 수정</h3><ul>
<li>GreaterThan 및 GreaterThanEqual 비교에 대한 Trie 인덱스 범위 연산 문제 해결<a href="https://github.com/milvus-io/milvus/pull/36126">(#36126</a>)</li>
<li>트라이 인덱스 구성에서 <code translate="no">marisa_label_order</code> 사용 수정<a href="https://github.com/milvus-io/milvus/pull/36060">(#36060</a>)</li>
<li><code translate="no">trie.predictive_search</code> 값 검사 개선<a href="https://github.com/milvus-io/milvus/pull/35999">(#35999</a>)</li>
<li>반전된 인덱스에서 이진 산술 표현식 지원 활성화<a href="https://github.com/milvus-io/milvus/pull/36097">(#36097</a>).</li>
<li>스킵인덱스로 인한 세그먼트 오류 수정<a href="https://github.com/milvus-io/milvus/pull/35908">(#35908</a>)</li>
<li>프록시 메타 캐시에서 메모리 누수 해결<a href="https://github.com/milvus-io/milvus/pull/36076">(#36076</a>)</li>
<li>디렉터리 충돌을 방지하기 위해 mmap 파일 경로 이름 변경<a href="https://github.com/milvus-io/milvus/pull/35975">(#35975</a>)</li>
<li>믹스 압축에서 실패/시간 초과 작업에 대한 로깅 및 정리 개선<a href="https://github.com/milvus-io/milvus/pull/35967">(#35967</a>).</li>
<li>위임자가 메모리를 많이 사용하는 동안 논리 교착 상태 해결<a href="https://github.com/milvus-io/milvus/pull/36066">(#36066</a>).</li>
<li>압축으로 모든 삽입이 삭제될 때 빈 세그먼트 생성 구현<a href="https://github.com/milvus-io/milvus/pull/36045">(#36045</a>)</li>
<li>2.4의 이전 버전 로드 정보에서 로드 필드 목록 채우기 수정<a href="https://github.com/milvus-io/milvus/pull/36018">(#36018</a>)</li>
<li>2.4에서 추적 구성 업데이트 로직 수정<a href="https://github.com/milvus-io/milvus/pull/35998">(#35998</a>)</li>
<li>동적 파티션 릴리스 중 검색/쿼리 요청 실패 해결<a href="https://github.com/milvus-io/milvus/pull/36019">(#36019</a>)</li>
<li>폴백 매개변수의 재정의 방지<a href="https://github.com/milvus-io/milvus/pull/36006">(#36006</a>)</li>
<li>유효성 검사를 위한 적절한 권한 그룹 등록 보장<a href="https://github.com/milvus-io/milvus/pull/35938">(#35938</a>)</li>
<li>DB 리미터 노드의 잘못된 정리 방지<a href="https://github.com/milvus-io/milvus/pull/35992">(#35992</a>)</li>
<li>장애 복구 후 복제본이 쿼리에 참여하지 않는 문제 해결<a href="https://github.com/milvus-io/milvus/pull/35925">(#35925</a>)</li>
<li>클러스터링 압축 쓰기에서 데이터 경합 해결<a href="https://github.com/milvus-io/milvus/pull/35958">(#35958</a>)</li>
<li>이동 작업 후 변수 참조 수정<a href="https://github.com/milvus-io/milvus/pull/35904">(#35904</a>)</li>
<li>클러스터링 키 스킵 로드 동작 검사 구현<a href="https://github.com/milvus-io/milvus/pull/35899">(#35899</a>)</li>
<li>2.4에서 쿼리코드 옵저버의 단일 시작 보장<a href="https://github.com/milvus-io/milvus/pull/35817">(#35817</a>)</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">개선 사항</h3><ul>
<li>Milvus 및 프로토 버전을 2.4.11로 업그레이드<a href="https://github.com/milvus-io/milvus/pull/36069">(#36069</a>).</li>
<li>단위 테스트에서 메모리 누수 문제 해결 및 단위 테스트 빌드에 use_asan 옵션 활성화<a href="https://github.com/milvus-io/milvus/pull/35857">(#35857</a>).</li>
<li>l0segmentsrowcount 제한을 보다 적절한 값으로 조정<a href="https://github.com/milvus-io/milvus/pull/36015">(#36015</a>).</li>
<li>델타로그 메모리 추정 계수를 1로 수정<a href="https://github.com/milvus-io/milvus/pull/36035">(#36035</a>).</li>
<li>로드 필드 목록 비교를 위한 슬라이스셋퀄 구현<a href="https://github.com/milvus-io/milvus/pull/36062">(#36062</a>).</li>
<li>삭제 작업의 로그 빈도 감소<a href="https://github.com/milvus-io/milvus/pull/35981">(#35981</a>)</li>
<li>etcd 버전을 3.5.14로 업그레이드<a href="https://github.com/milvus-io/milvus/pull/35977">(#35977</a>)</li>
<li>워밍업 후 MMAP-RSS 감소 최적화<a href="https://github.com/milvus-io/milvus/pull/35965">(#35965</a>)</li>
<li>읽기 요청에 대한 속도 제한기에서 냉각 오프 기간 제거<a href="https://github.com/milvus-io/milvus/pull/35936">(#35936</a>)</li>
<li>이전에 로드된 컬렉션에 대한 로드 필드 검사 개선<a href="https://github.com/milvus-io/milvus/pull/35910">(#35910</a>)</li>
<li>2.4에서 권한 목록과 관련된 역할 삭제 지원 추가<a href="https://github.com/milvus-io/milvus/pull/35863">(#35863)</a></li>
<li>더 이상 사용되지 않는 프로토 라이브러리 사용을 금지하는 depguard 규칙 구현<a href="https://github.com/milvus-io/milvus/pull/35818">(#35818</a>).</li>
</ul>
<h3 id="Others" class="common-anchor-header">기타</h3><ul>
<li>Knowhere 버전 업데이트<a href="https://github.com/milvus-io/milvus/pull/36067">(#36067</a>)</li>
</ul>
<h2 id="v2410" class="common-anchor-header">v2.4.10<button data-href="#v2410" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜 2024년 8월 30일</p>
<table>
<thead>
<tr><th>Milvus 버전</th><th>Python SDK 버전</th><th>Java SDK 버전</th><th>Node.js SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.10</td><td>2.4.6</td><td>2.4.3</td><td>2.4.6</td></tr>
</tbody>
</table>
<p>Milvus 2.4.10은 기능 및 안정성이 크게 개선되었습니다. 주요 기능으로는 AutoID 사용 컬렉션에 대한 업서트 작업 지원, 부분 컬렉션 로딩 기능, 메모리 사용량 최적화를 위한 다양한 메모리 매핑(MMAP) 구성 등이 있습니다. 이번 릴리스에서는 패닉, 코어 덤프, 리소스 누수를 유발하는 여러 버그도 해결되었습니다. 이러한 개선 사항을 최대한 활용하려면 업그레이드를 권장합니다.</p>
<h3 id="Features" class="common-anchor-header">주요 기능</h3><ul>
<li><strong>자동 ID를 사용한 업서트</strong>: 자동 ID 생성을 통한 업서트 작업 지원<a href="https://github.com/milvus-io/milvus/pull/34633">(#34633</a>)</li>
<li><strong>필드 부분 로드 수집</strong> [베타 프리뷰]: 컬렉션의 특정 필드 로드 허용<a href="https://github.com/milvus-io/milvus/pull/35696">(#35696</a>)</li>
<li><strong>RBAC 개선 사항</strong>:<ul>
<li>변경 데이터 캡처(CDC)에 대한 RBAC 메시지 지원 추가<a href="https://github.com/milvus-io/milvus/pull/35562">(#35562</a>)</li>
<li>읽기 전용/읽기/관리 권한 그룹을 도입하여 RBAC 부여 프로세스 간소화<a href="https://github.com/milvus-io/milvus/pull/35543">(#35543</a>)</li>
<li>RBAC 구성 백업 및 복원을 위한 새로운 API<a href="https://github.com/milvus-io/milvus/pull/35513">(#35513</a>)</li>
<li>RBAC 메타데이터 복원 후 프록시 캐시 새로 고침<a href="https://github.com/milvus-io/milvus/pull/35636">(#35636</a>)</li>
</ul></li>
<li><strong>MMAP 구성 개선</strong>: MMAP 동작을 제어하기 위한 보다 일반적인 구성 옵션<a href="https://github.com/milvus-io/milvus/pull/35609">(#35609</a>)</li>
<li><strong>데이터베이스 액세스 제한</strong>: 데이터베이스에 대한 읽기 액세스를 제한하는 새로운 속성<a href="https://github.com/milvus-io/milvus/pull/35754">(#35754</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">버그 수정</h3><ul>
<li>Arrow Go 클라이언트가 오류를 반환하지 않는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/35820">(#35820</a>)</li>
<li>부정확한 속도 제한 수정<a href="https://github.com/milvus-io/milvus/pull/35700">(#35700</a>)</li>
<li>가져오기 관련 API 실패 후 프록시 패닉 해결<a href="https://github.com/milvus-io/milvus/pull/35559">(#35559</a>)</li>
<li>GC 채널 체크포인트 중 실수로 삭제될 수 있는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/35708">(#35708</a>)</li>
<li>빈 후보 임포트 세그먼트로 인한 패닉 해결<a href="https://github.com/milvus-io/milvus/pull/35674">(#35674</a>)</li>
<li>MMAP 메모리 할당 해제 수정<a href="https://github.com/milvus-io/milvus/pull/35726">(#35726</a>)</li>
<li>2.2에서 2.4로 업그레이드 시 적절한 채널 감시 보장<a href="https://github.com/milvus-io/milvus/pull/35695">(#35695</a>)</li>
<li>데이터노드 감시 해제 채널 해제 기능 수정<a href="https://github.com/milvus-io/milvus/pull/35657">(#35657</a>)</li>
<li>루트코드 메타데이터의 파티션 수 수정<a href="https://github.com/milvus-io/milvus/pull/35601">(#35601</a>)</li>
<li>특정 파라미터에 대한 동적 구성 업데이트 관련 문제 해결<a href="https://github.com/milvus-io/milvus/pull/35637">(#35637</a>)</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">개선 사항</h3><h4 id="Performance" class="common-anchor-header">성능</h4><ul>
<li>동적 필드에서 검색 최적화<a href="https://github.com/milvus-io/milvus/pull/35602">(#35602</a>)</li>
<li>AVX512의 비트 세트 성능 개선<a href="https://github.com/milvus-io/milvus/pull/35480">(#35480</a>)</li>
<li>효율성 향상을 위해 <code translate="no">once</code> 초기화 후 값 다시 읽기<a href="https://github.com/milvus-io/milvus/pull/35643">(#35643</a>)</li>
</ul>
<h4 id="Rolling-upgrade-improvements" class="common-anchor-header">롤링 업그레이드 개선</h4><ul>
<li>일시 중단 후 쿼리 노드를 읽기 전용으로 표시<a href="https://github.com/milvus-io/milvus/pull/35586">(#35586</a>)</li>
<li>이전 코디네이터와 새 노드/프록시의 공존 방지<a href="https://github.com/milvus-io/milvus/pull/35760">(#35760</a>)</li>
</ul>
<h4 id="Others" class="common-anchor-header">기타</h4><ul>
<li>Milvus 코어 빌드 프로세스 최적화<a href="https://github.com/milvus-io/milvus/pull/35660">(#35660</a>)</li>
<li>프로토부프-고 v2로 업데이트<a href="https://github.com/milvus-io/milvus/pull/35555">(#35555</a>)</li>
<li>트레이스드 및 스패니드에 대한 16진수 문자열 인코딩으로 향상된 추적<a href="https://github.com/milvus-io/milvus/pull/35568">(#35568</a>)</li>
<li>쿼리 후크에 대한 히트 세그먼트 번호 메트릭 추가<a href="https://github.com/milvus-io/milvus/pull/35619">(#35619</a>)</li>
<li>로드 매개변수 구성 기능에 대한 이전 SDK와의 호환성 개선<a href="https://github.com/milvus-io/milvus/pull/35573">(#35573</a>)</li>
<li>HTTP v1/v2 스로틀링 지원 추가<a href="https://github.com/milvus-io/milvus/pull/35504">(#35504</a>)</li>
<li>인덱스 메모리 추정 수정<a href="https://github.com/milvus-io/milvus/pull/35670">(#35670</a>)</li>
<li>큰 세그먼트 생성을 피하기 위해 믹스 컴팩터에 여러 세그먼트를 쓰는 기능<a href="https://github.com/milvus-io/milvus/pull/35648">(#35648</a>).</li>
</ul>
<h2 id="v249" class="common-anchor-header">v2.4.9<button data-href="#v249" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜: 2024년 8월 20일</p>
<table>
<thead>
<tr><th>Milvus 버전</th><th>Python SDK 버전</th><th>Java SDK 버전</th><th>Node.js SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.9</td><td>2.4.5</td><td>2.4.3</td><td>2.4.4</td></tr>
</tbody>
</table>
<p>Milvus v2.4.9는 일부 코너 케이스에서 제한(topk) 미만의 결과를 반환할 수 있는 중요한 문제를 해결하고 플랫폼의 성능과 사용성을 향상시키기 위한 몇 가지 주요 개선 사항을 포함합니다.</p>
<h3 id="Critical-fixes" class="common-anchor-header">중요한 수정 사항</h3><ul>
<li>읽기 가능한 스냅샷에서 l0 세그먼트 제외<a href="https://github.com/milvus-io/milvus/pull/35510">(#35510)</a>.</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">개선 사항</h3><ul>
<li>프록시에서 중복된 스키마 헬퍼 생성을 제거했습니다<a href="https://github.com/milvus-io/milvus/pull/35502">(#35502)</a>.</li>
<li>우분투 20.04에서 Milvus 컴파일 지원 추가<a href="https://github.com/milvus-io/milvus/pull/35457">(#35457)</a>.</li>
<li>잠금 사용을 최적화하고 이중 플러시 클러스터링 버퍼 쓰기<a href="https://github.com/milvus-io/milvus/pull/35490">(#35490</a>)를 방지했습니다.</li>
<li>유효하지 않은 로그 제거<a href="https://github.com/milvus-io/milvus/pull/35473">(#35473</a>).</li>
<li>클러스터링 압축 사용 가이드 문서<a href="https://github.com/milvus-io/milvus/pull/35428">(#35428</a>)를 추가했습니다.</li>
<li>스키마 도우미에서 동적 필드에 대한 지원을 추가했습니다<a href="https://github.com/milvus-io/milvus/pull/35469">(#35469</a>).</li>
<li>생성된 YAML에 msgchannel 섹션을 추가했습니다<a href="https://github.com/milvus-io/milvus/pull/35466">(#35466)</a>.</li>
</ul>
<h2 id="v248" class="common-anchor-header">v2.4.8<button data-href="#v248" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜: 2024년 8월 14일</p>
<table>
<thead>
<tr><th>Milvus 버전</th><th>Python SDK 버전</th><th>Java SDK 버전</th><th>Node.js SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.8</td><td>2.4.5</td><td>2.4.3</td><td>2.4.4</td></tr>
</tbody>
</table>
<p>Milvus 2.4.8은 시스템의 성능과 안정성에 몇 가지 중요한 개선 사항을 도입했습니다. 가장 눈에 띄는 기능은 지정된 클러스터링 키를 기반으로 대규모 컬렉션의 데이터를 재분배하여 검색 및 쿼리 효율성을 높이고 스캔하는 데이터의 양을 줄이는 클러스터링 압축의 구현입니다. 또한 압축은 샤드 데이터 노드에서 분리되어 모든 데이터 노드가 독립적으로 압축을 수행할 수 있어 내결함성, 안정성, 성능, 확장성이 향상되었습니다. 또한, Go와 C++ 구성 요소 간의 인터페이스가 비동기 CGO 호출을 사용하도록 리팩터링되어 세션 시간 초과와 같은 문제를 해결했으며, 프로파일링을 기반으로 여러 가지 다른 성능 최적화가 이루어졌습니다. 애플리케이션 종속성도 업데이트되어 알려진 보안 취약점을 해결했습니다. 또한 이번 릴리스에는 수많은 성능 최적화와 중요한 버그 수정도 포함되어 있습니다.</p>
<h3 id="Features" class="common-anchor-header">주요 기능</h3><ul>
<li>클러스터링 압축을 구현하여 지정된 클러스터링 키를 기반으로 데이터를 재분배하여 쿼리 효율성을 향상시킬 수 있습니다<a href="https://github.com/milvus-io/milvus/pull/34326">(#34326</a>),<a href="https://github.com/milvus-io/milvus/pull/34363">(#34363</a>).</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">개선 사항</h3><ul>
<li>CGO에서 비동기 검색 및 검색 기능을 구현했습니다.<a href="https://github.com/milvus-io/milvus/pull/34200">(#34200</a>)</li>
<li>압축 프로세스를 샤드 데이터 노드에서 분리하여 시스템 모듈성을 개선했습니다.<a href="https://github.com/milvus-io/milvus/pull/34157">(#34157</a>)</li>
<li>프록시/위임자 내 쿼리 노드에서 클라이언트 풀링 지원을 추가하여 성능을 향상시켰습니다.<a href="https://github.com/milvus-io/milvus/pull/35195">(#35195</a>)</li>
<li>Gin 및 RestfulV1 핸들러에서 JSON 마샬링 및 언마샬링 중 CPU 오버헤드를 최소화하기 위해 Sonic을 통합했습니다.<a href="https://github.com/milvus-io/milvus/pull/35018">(#35018</a>)</li>
<li>인증 결과 검색을 최적화하기 위해 인메모리 캐시를 도입했습니다.<a href="https://github.com/milvus-io/milvus/pull/35272">(#35272</a>)</li>
<li>자동 인덱스의 기본 메트릭 유형을 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/34277">[#34277</a>, <a href="https://github.com/milvus-io/milvus/pull/34479">#34479</a>]</li>
<li>가변 열에 대한 런타임 메모리 형식을 리팩터링하여 메모리 사용량을 줄였습니다.<a href="https://github.com/milvus-io/milvus/pull/34367">[#34367</a>, <a href="https://github.com/milvus-io/milvus/pull/35012">#35012</a>, <a href="https://github.com/milvus-io/milvus/pull/35041">#35041</a>]</li>
<li>영구 데이터 저장이 가능하도록 압축 프로세스를 리팩터링했습니다.<a href="https://github.com/milvus-io/milvus/pull/34268">(#34268</a>)</li>
<li>증가하는 세그먼트에 대한 메모리 매핑 파일 지원을 활성화하여 메모리 관리를 개선했습니다.<a href="https://github.com/milvus-io/milvus/pull/34110">(#34110</a>)</li>
<li>RESTful API 지원, 로깅 일관성 수준, 시스템 오류와 사용자 오류 구분을 추가하여 액세스 로그를 개선했습니다.<a href="https://github.com/milvus-io/milvus/pull/34295">[#34295</a>, <a href="https://github.com/milvus-io/milvus/pull/34352">#34352</a>, <a href="https://github.com/milvus-io/milvus/pull/34396">#34396</a>]</li>
<li>Knowhere에서 새로운 <code translate="no">range_search_k</code> 매개변수를 활용하여 범위 검색 속도를 높였습니다.<a href="https://github.com/milvus-io/milvus/pull/34709">(#34709</a>)</li>
<li>필터 구성 및 쿼리 속도를 향상시키기 위해 차단된 블룸 필터를 적용했습니다.<a href="https://github.com/milvus-io/milvus/pull/34377">[#34377</a>, <a href="https://github.com/milvus-io/milvus/pull/34922">#34922</a>]</li>
<li>메모리 사용량 개선:<ul>
<li>데이터노드 삽입 버퍼를 위한 사전 할당된 공간.<a href="https://github.com/milvus-io/milvus/pull/34205">(#34205</a>)</li>
<li>Reduce 작업을 위한 <code translate="no">FieldData</code> 사전 할당.<a href="https://github.com/milvus-io/milvus/pull/34254">(#34254</a>)</li>
<li>메모리 누수를 방지하기 위해 삭제 코덱에서 레코드 해제.<a href="https://github.com/milvus-io/milvus/pull/34506">(#34506</a>)</li>
<li>파일 로드 중 디스크 파일 관리자의 동시성 수준 제어.<a href="https://github.com/milvus-io/milvus/pull/35282">(#35282</a>)</li>
<li>적시에 메모리를 해제할 수 있도록 Go 런타임 가비지 컬렉션 로직 최적화.<a href="https://github.com/milvus-io/milvus/pull/34950">(#34950</a>)</li>
<li>증가하는 세그먼트에 대한 새로운 봉인 정책을 구현했습니다.<a href="https://github.com/milvus-io/milvus/pull/34779">(#34779</a>)</li>
</ul></li>
<li>데이터코드 개선:<ul>
<li>CPU 사용량 감소.<a href="https://github.com/milvus-io/milvus/pull/34231">[#34231</a>, <a href="https://github.com/milvus-io/milvus/pull/34309">#34309</a>]</li>
<li>더 빠른 가비지 컬렉션 종료 로직을 구현했습니다.<a href="https://github.com/milvus-io/milvus/pull/35051">(#35051</a>)</li>
<li>워커 노드 스케줄링 알고리즘 개선.<a href="https://github.com/milvus-io/milvus/pull/34382">(#34382</a>)</li>
<li>가져오기 작업을 위한 향상된 세그먼트 크기 제어 알고리즘.<a href="https://github.com/milvus-io/milvus/pull/35149">(#35149</a>)</li>
</ul></li>
<li>로드 밸런싱 알고리즘 개선:<ul>
<li>위임자의 메모리 과부하 계수를 줄였습니다.<a href="https://github.com/milvus-io/milvus/pull/35164">(#35164</a>)</li>
<li>델리게이터에 고정 메모리 크기 할당.<a href="https://github.com/milvus-io/milvus/pull/34600">(#34600</a>)</li>
<li>새로운 쿼리 노드에 대한 세그먼트 및 채널의 과도한 할당을 방지했습니다.<a href="https://github.com/milvus-io/milvus/pull/34245">(#34245</a>)</li>
<li>쿼리 코디네이터의 스케줄링 주기당 작업 수를 줄이면서 스케줄링 빈도를 증가시켰습니다.<a href="https://github.com/milvus-io/milvus/pull/34987">(#34987</a>)</li>
<li>데이터 노드에서 채널 밸런싱 알고리즘 개선.<a href="https://github.com/milvus-io/milvus/pull/35033">(#35033</a>)</li>
</ul></li>
<li>확장된 시스템 메트릭: 다음과 같은 특정 측면을 모니터링하기 위해 다양한 구성 요소에 걸쳐 새로운 메트릭을 추가했습니다:<ul>
<li>강제 거부 쓰기 상태.<a href="https://github.com/milvus-io/milvus/pull/34989">(#34989</a>)</li>
<li>대기열 대기 시간.<a href="https://github.com/milvus-io/milvus/pull/34788">(#34788</a>)</li>
<li>디스크 할당량.<a href="https://github.com/milvus-io/milvus/pull/35306">(#35306</a>)</li>
<li>작업 실행 시간.<a href="https://github.com/milvus-io/milvus/pull/35141">(#35141</a>)</li>
<li>빈로그 크기.<a href="https://github.com/milvus-io/milvus/pull/35235">(#35235</a>)</li>
<li>삽입 속도.<a href="https://github.com/milvus-io/milvus/pull/35188">(#35188</a>)</li>
<li>메모리 최고 수위.<a href="https://github.com/milvus-io/milvus/pull/35188">(#35188</a>)</li>
<li>RESTful API 메트릭.<a href="https://github.com/milvus-io/milvus/pull/35083">(#35083</a>)</li>
<li>검색 지연 시간.<a href="https://github.com/milvus-io/milvus/pull/34783">(#34783</a>)</li>
</ul></li>
</ul>
<h3 id="Changes" class="common-anchor-header">변경 사항</h3><ul>
<li><p>오픈 소스 사용자의 경우 이 버전에서는 <code translate="no">FloatVector</code> 및 <code translate="no">BinaryVector</code> 에 대한 자동 인덱스의 메트릭 유형이 각각 <code translate="no">Cosine</code> 및 <code translate="no">Hamming</code> 로 변경됩니다.</p></li>
<li><p><strong>타사 종속성 버전 수정</strong>:</p>
<ul>
<li>이번 릴리스에서는 특정 타사 종속성 라이브러리에 대한 고정 버전이 도입되어 Milvus의 소프트웨어 공급망 관리가 크게 향상되었습니다.</li>
<li>프로젝트를 업스트림 변경 사항으로부터 격리하여 잠재적인 중단으로부터 일일 빌드를 보호합니다.</li>
<li>이 업데이트는 검증된 C++ 타사 패키지를 JFrog Cloud에서 독점적으로 호스팅하고 코난 레시피 리비전(RREV)을 활용함으로써 안정성을 보장합니다.</li>
<li>이 접근 방식은 코난센터의 업데이트로 인한 변경 사항 중단의 위험을 완화합니다.</li>
<li>우분투 22.04를 사용하는 개발자는 이러한 변경 사항의 혜택을 즉시 누릴 수 있습니다. 그러나 다른 운영 체제를 사용하는 개발자는 호환성 문제를 피하기 위해 <code translate="no">glibc</code> 버전을 업그레이드해야 할 수 있습니다.</li>
</ul></li>
</ul>
<h3 id="Critical-bug-fixes" class="common-anchor-header">중요한 버그 수정</h3><ul>
<li>L0 압축 중 세그먼트가 생략되어 삭제 데이터가 손실되던 문제를 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/33980">[#33980</a>, <a href="https://github.com/milvus-io/milvus/pull/34363">#34363</a>]</li>
<li>잘못된 데이터 범위 처리로 인해 삭제 메시지가 전달되지 않던 문제를 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/35313">(#35313</a>)</li>
<li><code translate="no">mmap</code> 의 잘못된 사용으로 인해 발생하는 SIGBUS 예외를 해결했습니다.<a href="https://github.com/milvus-io/milvus/pull/34455">[#34455</a>, <a href="https://github.com/milvus-io/milvus/pull/34530">#34530</a>]</li>
<li>잘못된 검색 표현식으로 인해 발생하는 충돌을 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/35307">(#35307</a>)</li>
<li>감시 컨텍스트에서 잘못된 시간 초과 설정으로 인해 데이터 노드 감시가 실패하는 문제를 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/35017">(#35017</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">버그 수정</h3><ul>
<li>특정 종속성을 업그레이드하여 보안 취약성을 해결했습니다.<a href="https://github.com/milvus-io/milvus/pull/33927">[#33927</a>, <a href="https://github.com/milvus-io/milvus/pull/34693">#34693</a>]</li>
<li>지나치게 긴 표현식으로 인해 트리거되는 구문 분석 오류를 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/34957">(#34957</a>)</li>
<li>쿼리 계획 구문 분석 중에 발생하는 메모리 누수를 해결했습니다.<a href="https://github.com/milvus-io/milvus/pull/34932">(#34932</a>)</li>
<li>동적 로그 수준 수정이 적용되지 않던 문제를 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/34777">(#34777</a>)</li>
<li>초기화되지 않은 세그먼트 오프셋으로 인해 증가하는 데이터에 대한 쿼리 기준 그룹화가 실패하는 문제를 해결했습니다.<a href="https://github.com/milvus-io/milvus/pull/34750">(#34750</a>)</li>
<li>Knowhere 반복기를 사용할 때 검색 매개변수 설정을 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/34732">(#34732</a>)</li>
<li>파티션 로드 상태를 확인하는 로직을 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/34305">(#34305</a>)</li>
<li>처리되지 않은 요청 오류로 인해 권한 캐시 업데이트가 실패하는 문제를 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/34697">(#34697</a>)</li>
<li>쿼리코드 재시작 후 로드된 컬렉션 복구에 실패하는 문제를 해결했습니다.<a href="https://github.com/milvus-io/milvus/pull/35211">(#35211</a>)</li>
<li>불필요한 인덱스 매개변수 유효성 검사를 제거하여 로드 무력화 문제를 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/35179">(#35179</a>)</li>
<li><code translate="no">compressBinlog</code> 이 실행되어 <code translate="no">reloadFromKV</code> 이 빈로그의 <code translate="no">logID</code> 을 제대로 채울 수 있도록 했습니다.<a href="https://github.com/milvus-io/milvus/pull/34062">(#34062</a>)</li>
<li>DataCoord에서 가비지 수집 후 수집 메타데이터가 제거되지 않던 문제를 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/34884">(#34884</a>)</li>
<li>가져오기를 통해 생성된 플러시 세그먼트를 제거하여 DataCoord 내 SegmentManager의 메모리 누수를 해결했습니다.<a href="https://github.com/milvus-io/milvus/pull/34651">(#34651</a>)</li>
<li>압축이 비활성화되고 컬렉션이 삭제될 때 발생하는 패닉 문제를 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/34206">(#34206</a>)</li>
<li>메모리 사용량 추정 알고리즘을 개선하여 데이터 노드에서 메모리 부족 문제를 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/34203">(#34203</a>)</li>
<li>청크 캐시에 단일 비행을 구현하여 여러 벡터 검색 요청이 캐시 미스에 도달했을 때 버스트 메모리 사용을 방지했습니다.<a href="https://github.com/milvus-io/milvus/pull/34283">(#34283</a>)</li>
<li>구성에서 CAS(비교 및 스왑) 작업 중 <code translate="no">ErrKeyNotFound</code> 을 캡처했습니다.<a href="https://github.com/milvus-io/milvus/pull/34489">(#34489</a>)</li>
<li>CAS 작업에서 포맷된 값을 실수로 사용하여 구성 업데이트가 실패하는 문제를 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/34373">(#34373</a>)</li>
</ul>
<h3 id="Miscellaneous" class="common-anchor-header">기타</h3><ul>
<li>통합 가시성 및 모니터링 기능을 향상시키는 OTLP HTTP 내보내기 지원이 추가되었습니다.<a href="https://github.com/milvus-io/milvus/pull/35073">[#35073</a>, <a href="https://github.com/milvus-io/milvus/pull/35299">#35299</a>]</li>
<li>이제 동적으로 수정할 수 있는 '최대 컬렉션' 및 '디스크 할당량'과 같은 속성을 도입하여 데이터베이스 기능을 개선했습니다.<a href="https://github.com/milvus-io/milvus/pull/34511">[#34511</a>, <a href="https://github.com/milvus-io/milvus/pull/34386">#34386</a>]</li>
<li>진단 및 모니터링을 개선하기 위해 DataNode 내에서 L0 압축 프로세스에 대한 추적 기능을 추가했습니다.<a href="https://github.com/milvus-io/milvus/pull/33898">(#33898</a>)</li>
<li>컬렉션당 L0 세그먼트 항목 수에 대한 할당량 구성을 도입하여, 역압력을 적용하여 삭제율을 더 잘 제어할 수 있게 되었습니다.<a href="https://github.com/milvus-io/milvus/pull/34837">(#34837</a>)</li>
<li>삽입 작업에 대한 속도 제한 메커니즘을 업서트 작업에도 적용하도록 확장하여 부하가 높을 때에도 일관된 성능을 보장합니다.<a href="https://github.com/milvus-io/milvus/pull/34616">(#34616</a>)</li>
<li>프록시 CGO 호출을 위한 동적 CGO 풀을 구현하여 리소스 사용량과 성능을 최적화했습니다.<a href="https://github.com/milvus-io/milvus/pull/34842">(#34842</a>)</li>
<li>우분투, 록키 및 아마존 운영 체제에서 DiskAnn 컴파일 옵션을 활성화하여 이러한 플랫폼에서의 호환성 및 성능을 개선했습니다.<a href="https://github.com/milvus-io/milvus/pull/34244">(#34244</a>)</li>
<li>Conan을 1.64.1 버전으로 업그레이드하여 최신 기능 및 개선 사항과의 호환성을 보장합니다.<a href="https://github.com/milvus-io/milvus/pull/35216">(#35216</a>)</li>
<li>Knowhere를 2.3.7 버전으로 업데이트하여 성능 향상과 새로운 기능을 추가했습니다.<a href="https://github.com/milvus-io/milvus/pull/34709">(#34709</a>)</li>
<li>일관된 빌드를 보장하고 예기치 않은 변경의 위험을 줄이기 위해 특정 타사 패키지의 리비전을 수정했습니다.<a href="https://github.com/milvus-io/milvus/pull/35316">(#35316</a>)</li>
</ul>
<h2 id="v246" class="common-anchor-header">v2.4.6<button data-href="#v246" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜: 2024년 7월 16일</p>
<table>
<thead>
<tr><th>Milvus 버전</th><th>Python SDK 버전</th><th>Java SDK 버전</th><th>Node.js SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.6</td><td>2.4.4</td><td>2.4.2</td><td>2.4.4</td></tr>
</tbody>
</table>
<p>Milvus v2.4.6은 삭제 중 패닉, 메모리 누수, 데이터 손실과 같은 중요한 문제를 해결하는 버그 수정 릴리스입니다. 또한 모니터링 메트릭 개선, Go 버전 1.21 업그레이드, RESTful 카운트(*) 쿼리 사용자 환경 개선 등 여러 가지 최적화 기능도 도입되었습니다.</p>
<h3 id="Improvements" class="common-anchor-header">개선 사항</h3><ul>
<li>RESTful API 쿼리의 사용자 편의성이 향상되었습니다<a href="https://github.com/milvus-io/milvus/pull/34444">(#34444</a>).</li>
<li>Go 버전이 1.20에서 1.21로 업그레이드되었습니다<a href="https://github.com/milvus-io/milvus/pull/33940">(#33940</a>).</li>
<li>히스토그램 메트릭 버킷을 최적화하여 버킷을 더 세분화했습니다<a href="https://github.com/milvus-io/milvus/pull/34592">(#34592</a>).</li>
<li>Pulsar 종속성 버전을 2.8.2에서 2.9.5로 업그레이드했습니다. Milvus 2.4.6부터는 Pulsar를 2.9.5로 업그레이드하는 것이 좋습니다.</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">버그 수정</h3><ul>
<li>GetReplicas API가 nil 상태를 반환하는 문제를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/34019">(#34019</a>).</li>
<li>쿼리가 삭제된 레코드를 반환할 수 있는 문제를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/34502">(#34502</a>).</li>
<li>잘못된 수명 제어로 인해 인덱스노드가 중지되는 동안 멈추는 문제를 해결했습니다<a href="https://github.com/milvus-io/milvus/pull/34559">(#34559</a>).</li>
<li>워커가 오프라인 상태일 때 기본 키 오라클 객체의 메모리 누수를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/34020">(#34020</a>).</li>
<li>루프 종료 시 매개변수 캡처 문제를 해결하여 올바른 노드에 알릴 수 있도록 ChannelManagerImplV2를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/34004">(#34004</a>).</li>
<li>딥 카피<a href="https://github.com/milvus-io/milvus/pull/34126">(#34126)</a>를 구현하여 ImportTask segmentsInfo의 읽기-쓰기 데이터 경합을 수정했습니다.</li>
<li>롤링 업그레이드 중 오류를 방지하기 위해 "legacyVersionWithoutRPCWatch" 구성 옵션의 버전 정보를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/34185">(#34185</a>).</li>
<li>로드된 파티션 수에 대한 메트릭을 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/34195">(#34195</a>).</li>
<li>세그코어 추적을 설정할 때 <code translate="no">otlpSecure</code> 구성을 전달했습니다<a href="https://github.com/milvus-io/milvus/pull/34210">(#34210</a>).</li>
<li>DataCoord의 속성을 실수로 덮어쓰는 문제를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/34240">(#34240</a>).</li>
<li>새로 생성된 두 개의 메시지 스트림이 잘못 병합되어 발생하는 데이터 손실 문제를 해결했습니다<a href="https://github.com/milvus-io/milvus/pull/34563">(#34563</a>).</li>
<li>메시지 스트림이 잘못된 p채널을 사용하려고 할 때 발생하는 패닉 현상을 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/34230">(#34230)</a>.</li>
<li>가져오기가 고아 파일을 생성할 수 있는 문제를 해결했습니다<a href="https://github.com/milvus-io/milvus/pull/34071">(#34071</a>).</li>
<li>세그먼트의 기본 키가 중복되어 쿼리 결과가 불완전한 문제를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/34302">(#34302</a>).</li>
<li>L0 압축에서 봉인된 세그먼트가 누락되는 문제를 해결했습니다<a href="https://github.com/milvus-io/milvus/pull/34566">(#34566</a>).</li>
<li>가비지 수집 후 생성된 채널-cp 메타에서 더티 데이터가 발생하는 문제를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/34609">(#34609</a>).</li>
<li>루트코드 재시작 후 database_num이 0인 메트릭을 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/34010">(#34010)</a>.</li>
<li>가져오기를 통해 생성된 플러시 세그먼트를 제거하여 DataCoord의 SegmentManager에서 메모리 누수를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/34652">(#34652</a>).</li>
<li>DataCoord가 재시작된 후 압축빈로그가 빈로그의 logID를 채우도록 하여 KV에서 제대로 다시 로드되도록 보장합니다<a href="https://github.com/milvus-io/milvus/pull/34064">(#34064)</a>.</li>
</ul>
<h2 id="v245" class="common-anchor-header">v2.4.5<button data-href="#v245" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜: 2024년 6월 18일</p>
<table>
<thead>
<tr><th>Milvus 버전</th><th>Python SDK 버전</th><th>Java SDK 버전</th><th>Node.js SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.5</td><td>2.4.4</td><td>2.4.1</td><td>2.4.3</td></tr>
</tbody>
</table>
<p>Milvus 2.4.5 릴리스에는 성능, 안정성 및 기능 향상을 위한 몇 가지 개선 사항과 버그 수정이 도입되었습니다. Milvus 2.4.5는 자동 인덱싱을 통해 스파스, float16, bfloat16 벡터 검색을 간소화하고, 블룸 필터 최적화를 통해 검색, 삭제, 압축 속도를 높이며, 로딩 시간 단축과 L0 세그먼트 가져오기 지원을 통해 데이터 관리 문제를 해결합니다. 또한 효율적인 고차원 스파스 데이터 검색을 위해 스파스 HNSW 인덱스를 도입하고, 스파스 플로트 벡터 지원으로 RESTful API를 개선하며, 안정성 향상을 위해 중요한 버그를 수정합니다.</p>
<h3 id="New-Features" class="common-anchor-header">새로운 기능</h3><ul>
<li>데이터베이스 API 설명/변경에 rbac 지원 추가<a href="https://github.com/milvus-io/milvus/pull/33804">(#33804</a>)</li>
<li>스파스 벡터에 대한 HNSW 인덱스 구축 지원<a href="https://github.com/milvus-io/milvus/pull/33653">(#33653</a>, <a href="https://github.com/milvus-io/milvus/pull/33662">#33662</a>)</li>
<li>바이너리 벡터에 대한 디스크 인덱스 구축 지원<a href="https://github.com/milvus-io/milvus/pull/33575">(#33575</a>).</li>
<li>RESTful v2에서 지원되는 스파스 벡터 유형<a href="https://github.com/milvus-io/milvus/pull/33555">(#33555</a>)</li>
<li>구성 요소를 중지하기 위해 /management/stop RESTful API 추가<a href="https://github.com/milvus-io/milvus/pull/33799">(#33799</a>).</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">개선 사항</h3><ul>
<li>maxPartitionNum 기본값을 1024로 설정<a href="https://github.com/milvus-io/milvus/pull/33950">(#33950</a>).</li>
<li>사용할 수 없는 오류 발생 시 연결 강제 재설정 활성화<a href="https://github.com/milvus-io/milvus/pull/33910">(#33910</a>)</li>
<li>수집 레벨의 플러시 속도 제한기 활성화<a href="https://github.com/milvus-io/milvus/pull/33864">(#33864</a>)</li>
<li>세그먼트 예측 속도를 높이기 위해 블룸 필터 적용을 병렬로 실행<a href="https://github.com/milvus-io/milvus/pull/33793">(#33793</a>).</li>
<li>삭제 로그 언마샬에 fastjson lib를 사용하여 json.Unmarshal<a href="https://github.com/milvus-io/milvus/pull/33802">(#33802</a>) 속도 향상.</li>
<li>블룸 필터 함수 호출 비용을 줄이기 위해 BatchPkExist를 사용<a href="https://github.com/milvus-io/milvus/pull/33752">(#33752</a>).</li>
<li>작은 컬렉션의 로딩 속도 향상<a href="https://github.com/milvus-io/milvus/pull/33746">(#33746</a>)</li>
<li>L0 세그먼트로 데이터 삭제 가져오기 지원(<a href="https://github.com/milvus-io/milvus/pull/33712">#33712</a>)</li>
<li>동일한 작업을 반복해서 실행하는 aviod에 마크 압축 작업 시간 초과 건너뛰기<a href="https://github.com/milvus-io/milvus/pull/33833">(#33833</a>)</li>
<li>넘피 벌크 삽입에서 float16 및 bfloat16 벡터를 BinaryVector와 동일하게 처리 (<a href="https://github.com/milvus-io/milvus/pull/33788">#33788</a>).</li>
<li>seek 메서드에 includeCurrentMsg 플래그를 추가했습니다<a href="https://github.com/milvus-io/milvus/pull/33743">(#33743</a>).</li>
<li>mergeInterval, targetBufSize, msgdispatcher의 최대 허용 지연을 구성에 추가했습니다<a href="https://github.com/milvus-io/milvus/pull/33680">(#33680</a>).</li>
<li>스파스 벡터의 GetVectorByID 개선<a href="https://github.com/milvus-io/milvus/pull/33652">(#33652</a>).</li>
<li>불필요한 복사 및 함수 호출 비용을 줄이기 위해 StringPrimarykey를 제거했습니다 (<a href="https://github.com/milvus-io/milvus/pull/33649">#33649</a>).</li>
<li>바이너리/스파스 데이터 타입에 대한 자동 인덱스 매핑 추가<a href="https://github.com/milvus-io/milvus/pull/33625">(#33625</a>).</li>
<li>메모리 사용량을 줄이기 위해 일부 캐시 최적화<a href="https://github.com/milvus-io/milvus/pull/33560">(#33560</a>)</li>
<li>가져오기/사전 가져오기 작업을 위한 실행 인터페이스 추상화 (<a href="https://github.com/milvus-io/milvus/pull/33607">#33607</a>).</li>
<li>버퍼 삽입에서 맵 pk를 타임스탬프에 사용하여 bf 원인을 줄임<a href="https://github.com/milvus-io/milvus/pull/33582">(#33582</a>).</li>
<li>가져오기의 중복 메타 작업 방지(<a href="https://github.com/milvus-io/milvus/pull/33519">#33519</a>)</li>
<li>더 나은 디스크 할당량 정보 로깅, UseDefaultConsistency 플래그 추가, 불필요한 로그 제거를 통해 로그 개선<a href="https://github.com/milvus-io/milvus/pull/33597">(#33597</a>, <a href="https://github.com/milvus-io/milvus/pull/33644">#33644</a>, <a href="https://github.com/milvus-io/milvus/pull/33670">#33670</a>).</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">버그 수정</h3><ul>
<li>쿼리훅이 벡터 유형을 인식할 수 없는 버그 수정<a href="https://github.com/milvus-io/milvus/pull/33911">(#33911</a>)</li>
<li>캡처된 반복 변수 partitionID 사용 방지<a href="https://github.com/milvus-io/milvus/pull/33970">(#33970</a>)</li>
<li>밀버스가 바이너리 및 스파스 벡터에서 자동 인덱스를 생성할 수 없는 버그를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/33867">(#33867</a>).</li>
<li>모든 벡터의 잘못된 인덱스 파라미터에서 인덱스 노드가 인덱스 생성을 다시 시도할 수 있는 버그를 수정했습니다(<a href="https://github.com/milvus-io/milvus/pull/33878">#33878</a>).</li>
<li>로드와 릴리스가 동시에 발생하면 서버가 충돌할 수 있는 버그 수정<a href="https://github.com/milvus-io/milvus/pull/33699">(#33699</a>).</li>
<li>구성 값에 대한 캐시 일관성 개선<a href="https://github.com/milvus-io/milvus/pull/33797">(#33797</a>)</li>
<li>삭제 중 데이터 손실 가능성 방지<a href="https://github.com/milvus-io/milvus/pull/33821">(#33821</a>)</li>
<li>컬렉션 삭제 후 DroppedAt 필드(삭제 타임스탬프일 가능성이 있는)가 설정되도록 함<a href="https://github.com/milvus-io/milvus/pull/33767">(#33767</a>).</li>
<li>Milvus가 바이너리 벡터 데이터 크기를 잘못 처리할 수 있는 문제를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/33751">(#33751</a>).</li>
<li>민감한 Kafka 자격 증명이 일반 텍스트로 로그인되는 것을 방지했습니다.<a href="https://github.com/milvus-io/milvus/pull/33694">(#33694</a>, <a href="https://github.com/milvus-io/milvus/pull/33747">#33747</a>).</li>
<li>Milvus에서 여러 벡터 필드가 있는 데이터를 올바르게 가져올 수 있도록 수정.<a href="https://github.com/milvus-io/milvus/pull/33724">(#33724</a>)</li>
<li>시작하기 전에 가져오기 작업이 존재하는지 확인하여 가져오기 안정성을 향상시켰습니다.<a href="https://github.com/milvus-io/milvus/pull/33673">(#33673</a>)</li>
<li>희소 HNSW 인덱스 처리 개선(내부 기능)<a href="https://github.com/milvus-io/milvus/pull/33714">(#33714</a>)</li>
<li>메모리 누수를 방지하기 위해 벡터 메모리 정리<a href="https://github.com/milvus-io/milvus/pull/33708">(#33708</a>)</li>
<li>상태 잠금 문제를 수정하여 비동기 워밍업이 더 원활해졌습니다.<a href="https://github.com/milvus-io/milvus/pull/33687">(#33687</a>).</li>
<li>쿼리 이터레이터에서 결과가 누락될 수 있는 버그를 해결했습니다.<a href="https://github.com/milvus-io/milvus/pull/33506">(#33506</a>)</li>
<li>가져오기 세그먼트 크기가 고르지 않을 수 있는 버그를 수정했습니다(<a href="https://github.com/milvus-io/milvus/pull/33634">#33634</a>).</li>
<li>bf16, fp16 및 이진 벡터 유형에 대한 잘못된 데이터 크기 처리 수정<a href="https://github.com/milvus-io/milvus/pull/33488">(#33488</a>)</li>
<li>L0 압축기의 잠재적 문제를 해결하여 안정성 개선<a href="https://github.com/milvus-io/milvus/pull/33564">(#33564</a>)</li>
<li>동적 구성 업데이트가 캐시에 올바르게 반영되도록 보장.<a href="https://github.com/milvus-io/milvus/pull/33590">(#33590</a>)</li>
<li>RootCoordQuotaStates 메트릭의 정확성 개선(<a href="https://github.com/milvus-io/milvus/pull/33601">#33601</a>)</li>
<li>메트릭에서 로드된 엔티티의 수를 정확하게 보고하도록 보장<a href="https://github.com/milvus-io/milvus/pull/33522">(#33522</a>).</li>
<li>예외 로그에 보다 완전한 정보를 제공. <a href="https://github.com/milvus-io/milvus/pull/33396">(#33396</a>)</li>
<li>불필요한 그룹 검사기를 제거하여 쿼리 파이프라인 최적화<a href="https://github.com/milvus-io/milvus/pull/33485">(#33485</a>)</li>
<li>인덱스 노드에서 보다 정확한 디스크 용량 확인을 위해 로컬 스토리지 경로를 사용.<a href="https://github.com/milvus-io/milvus/pull/33505">(#33505</a>)</li>
<li>히트 횟수가 제한보다 클 때 hasMoreResult가 false를 반환할 수 있는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/33642">(#33642</a>)</li>
<li>워커에 더 이상 메모리가 없을 때 bfs가 반복해서 로드되는 것을 방지하기 위해 위임자에서 bf 로드 지연<a href="https://github.com/milvus-io/milvus/pull/33650">(#33650</a>)- 쿼리훅이 벡터 유형을 인식하지 못하는 버그 수정<a href="https://github.com/milvus-io/milvus/pull/33911">(#33911</a>).</li>
<li>캡처된 반복 변수 partitionID 사용 방지<a href="https://github.com/milvus-io/milvus/pull/33970">(#33970</a>)</li>
<li>밀버스가 바이너리 및 스파스 벡터에서 자동 인덱스를 생성할 수 없는 버그를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/33867">(#33867</a>).</li>
<li>모든 벡터의 잘못된 인덱스 파라미터에서 인덱스 노드가 인덱스 생성을 다시 시도할 수 있는 버그를 수정했습니다(<a href="https://github.com/milvus-io/milvus/pull/33878">#33878</a>).</li>
<li>로드와 릴리스가 동시에 발생하면 서버가 충돌할 수 있는 버그 수정<a href="https://github.com/milvus-io/milvus/pull/33699">(#33699</a>).</li>
<li>구성 값에 대한 캐시 일관성 개선<a href="https://github.com/milvus-io/milvus/pull/33797">(#33797</a>)</li>
<li>삭제 중 데이터 손실 가능성 방지<a href="https://github.com/milvus-io/milvus/pull/33821">(#33821</a>)</li>
<li>컬렉션 삭제 후 DroppedAt 필드(삭제 타임스탬프일 가능성이 있는)가 설정되도록 함<a href="https://github.com/milvus-io/milvus/pull/33767">(#33767</a>).</li>
<li>Milvus가 바이너리 벡터 데이터 크기를 잘못 처리할 수 있는 문제를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/33751">(#33751</a>).</li>
<li>민감한 Kafka 자격 증명이 일반 텍스트로 로그인되는 것을 방지했습니다.<a href="https://github.com/milvus-io/milvus/pull/33694">(#33694</a>, <a href="https://github.com/milvus-io/milvus/pull/33747">#33747</a>).</li>
<li>Milvus에서 여러 벡터 필드가 있는 데이터를 올바르게 가져올 수 있도록 수정.<a href="https://github.com/milvus-io/milvus/pull/33724">(#33724</a>)</li>
<li>시작하기 전에 가져오기 작업이 존재하는지 확인하여 가져오기 안정성을 향상시켰습니다.<a href="https://github.com/milvus-io/milvus/pull/33673">(#33673</a>)</li>
<li>희소 HNSW 인덱스 처리 개선(내부 기능)<a href="https://github.com/milvus-io/milvus/pull/33714">(#33714</a>)</li>
<li>메모리 누수를 방지하기 위해 벡터 메모리 정리<a href="https://github.com/milvus-io/milvus/pull/33708">(#33708</a>)</li>
<li>상태 잠금 문제를 수정하여 비동기 워밍업이 더 원활해졌습니다.<a href="https://github.com/milvus-io/milvus/pull/33687">(#33687</a>).</li>
<li>쿼리 이터레이터에서 결과가 누락될 수 있는 버그를 해결했습니다.<a href="https://github.com/milvus-io/milvus/pull/33506">(#33506</a>)</li>
<li>가져오기 세그먼트 크기가 고르지 않을 수 있는 버그를 수정했습니다(<a href="https://github.com/milvus-io/milvus/pull/33634">#33634</a>).</li>
<li>bf16, fp16 및 이진 벡터 유형에 대한 잘못된 데이터 크기 처리 수정<a href="https://github.com/milvus-io/milvus/pull/33488">(#33488</a>)</li>
<li>L0 압축기의 잠재적 문제를 해결하여 안정성 개선<a href="https://github.com/milvus-io/milvus/pull/33564">(#33564</a>)</li>
<li>동적 구성 업데이트가 캐시에 올바르게 반영되도록 보장.<a href="https://github.com/milvus-io/milvus/pull/33590">(#33590</a>)</li>
<li>RootCoordQuotaStates 메트릭의 정확성 개선(<a href="https://github.com/milvus-io/milvus/pull/33601">#33601</a>)</li>
<li>메트릭에서 로드된 엔티티의 수를 정확하게 보고하도록 보장<a href="https://github.com/milvus-io/milvus/pull/33522">(#33522</a>).</li>
<li>예외 로그에 보다 완전한 정보를 제공. <a href="https://github.com/milvus-io/milvus/pull/33396">(#33396</a>)</li>
<li>불필요한 그룹 검사기를 제거하여 쿼리 파이프라인 최적화<a href="https://github.com/milvus-io/milvus/pull/33485">(#33485</a>)</li>
<li>인덱스 노드에서 보다 정확한 디스크 용량 확인을 위해 로컬 스토리지 경로를 사용.<a href="https://github.com/milvus-io/milvus/pull/33505">(#33505</a>)</li>
<li>히트 횟수가 제한보다 클 때 hasMoreResult가 false를 반환할 수 있는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/33642">(#33642</a>)</li>
<li>워커에 더 이상 메모리가 없을 때 bfs가 반복해서 로드되는 것을 방지하기 위해 위임자에서 bf 로드 지연<a href="https://github.com/milvus-io/milvus/pull/33650">(#33650</a>)</li>
</ul>
<h2 id="v244" class="common-anchor-header">v2.4.4<button data-href="#v244" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜: 2024년 5월 31일</p>
<table>
<thead>
<tr><th>밀버스 버전</th><th>Python SDK 버전</th><th>Java SDK 버전</th><th>Node.js SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.4</td><td>2.4.3</td><td>2.4.1</td><td>2.4.2</td></tr>
</tbody>
</table>
<p>Milvus v2.4.4에는 성능과 안정성 향상을 위한 몇 가지 중요한 버그 수정 및 개선 사항이 포함되어 있습니다. 특히 <strong>대량 삽입 통계 로그가 잘못 가비지 수집되어</strong> 데이터 무결성에 영향을 미칠 수 있는 <strong>중대한 문제를 해결했습니다</strong>. <strong>모든 v2.4 사용자는 이 수정 사항을 활용하기 위해 이 버전으로 업그레이드할 것을 강력히 권장합니다.</strong></p>
<p><strong>대량 삽입을 사용 중인 경우 데이터 무결성을 위해 가능한 한 빨리 v2.4.4로 업그레이드하세요.</strong></p>
<h3 id="Critical-bug-fixes" class="common-anchor-header">중요한 버그 수정</h3><ul>
<li>통계 로그 ID 채우기 및 정확성 검증<a href="https://github.com/milvus-io/milvus/pull/33478">(#33478</a>)</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">개선 사항</h3><ul>
<li>ARM SVE용 비트셋 업그레이드<a href="https://github.com/milvus-io/milvus/pull/33440">(#33440</a>)</li>
<li>GCC-13으로 Milvus 컴파일 활성화<a href="https://github.com/milvus-io/milvus/pull/33441">(#33441</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">버그 수정</h3><ul>
<li>모든 권한이 부여된 경우 빈 컬렉션 표시<a href="https://github.com/milvus-io/milvus/pull/33454">(#33454</a>)</li>
<li>x86_64 뿐만 아니라 현재 플랫폼에 대한 CMake 다운로드 및 설치 보장<a href="https://github.com/milvus-io/milvus/pull/33439">(#33439</a>)</li>
</ul>
<h2 id="v243" class="common-anchor-header">v2.4.3<button data-href="#v243" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜: 2024년 5월 29일</p>
<table>
<thead>
<tr><th>Milvus 버전</th><th>Python SDK 버전</th><th>Java SDK 버전</th><th>Node.js SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.3</td><td>2.4.3</td><td>2.4.1</td><td>2.4.2</td></tr>
</tbody>
</table>
<p>Milvus 버전 2.4.3에는 성능과 안정성을 높이기 위한 다양한 기능, 개선 사항 및 버그 수정이 도입되었습니다. 주목할 만한 개선 사항으로는 스파스 플로트 벡터 대량 삽입 지원과 최적화된 블룸 필터 가속화가 있습니다. 동적 구성 업데이트부터 메모리 사용량 최적화까지 다양한 영역이 개선되었습니다. 버그 수정을 통해 패닉 시나리오와 같은 중요한 문제를 해결하고 보다 원활한 시스템 운영을 보장했습니다. 이번 릴리스는 기능 향상, 성능 최적화, 강력한 사용자 경험 제공을 위한 Milvus의 지속적인 노력을 강조했습니다.</p>
<h3 id="Features" class="common-anchor-header">주요 특징</h3><ul>
<li>빈로그/json/파켓에 대한 스파스 플로트 벡터 대량 삽입 지원<a href="https://github.com/milvus-io/milvus/pull/32649">(#32649</a>)</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">개선 사항</h3><ul>
<li>RPC 기반 데이터코드/노드 감시 채널 구현<a href="https://github.com/milvus-io/milvus/pull/32036">(#32036</a>)</li>
<li>삭제 필터링을 가속화하기 위해 최적화된 블룸 필터<a href="https://github.com/milvus-io/milvus/pull/32642">(#32642</a>, <a href="https://github.com/milvus-io/milvus/pull/33329">#33329</a>, <a href="https://github.com/milvus-io/milvus/pull/33284">#33284</a>)</li>
<li>스칼라 인덱스에 원시 데이터가 없는 경우 mmap을 통해 원시 데이터 로드<a href="https://github.com/milvus-io/milvus/pull/33317">(#33317</a>).</li>
<li>밀버스 구성을 milvus.yaml에 동기화<a href="https://github.com/milvus-io/milvus/pull/33322">(#33322</a>, <a href="https://github.com/milvus-io/milvus/pull/32920">#32920</a>, <a href="https://github.com/milvus-io/milvus/pull/32857">#32857</a>, <a href="https://github.com/milvus-io/milvus/pull/32946">#32946</a>).</li>
<li>knowhere 버전 업데이트<a href="https://github.com/milvus-io/milvus/pull/33310">(#33310</a>, <a href="https://github.com/milvus-io/milvus/pull/32931">#32931</a>, <a href="https://github.com/milvus-io/milvus/pull/33043">#33043</a>)</li>
<li>쿼리코드에서 밸런서 정책의 동적 업데이트 활성화<a href="https://github.com/milvus-io/milvus/pull/33272">(#33272</a>)</li>
<li>쓰기 버퍼에 미리 빌드된 로거를 사용하여 로거 할당 최소화<a href="https://github.com/milvus-io/milvus/pull/33304">(#33304</a>).</li>
<li>매개변수 검사 개선<a href="https://github.com/milvus-io/milvus/pull/32777">(#32777</a>, <a href="https://github.com/milvus-io/milvus/pull/33271">#33271</a>, <a href="https://github.com/milvus-io/milvus/pull/33218">#33218</a>)</li>
<li>체크포인트에서 잘못된 메시지 ID를 무시하는 매개변수 추가<a href="https://github.com/milvus-io/milvus/pull/33249">(#33249</a>).</li>
<li>플러그인에 대한 초기화 실패 처리를 제어하는 구성 추가<a href="https://github.com/milvus-io/milvus/pull/32680">(#32680</a>)</li>
<li>knowhere에 대한 점수 계산 일관성 설정 추가<a href="https://github.com/milvus-io/milvus/pull/32997">(#32997</a>).</li>
<li>공개 역할 권한의 초기화를 제어하는 구성 옵션 도입<a href="https://github.com/milvus-io/milvus/pull/33174">(#33174</a>).</li>
<li>필드 읽기 시 메모리 사용량 최적화<a href="https://github.com/milvus-io/milvus/pull/33196">(#33196</a>)</li>
<li>채널 매니저 v2의 구현 개선<a href="https://github.com/milvus-io/milvus/pull/33172">(#33172</a>, <a href="https://github.com/milvus-io/milvus/pull/33121">#33121</a>, <a href="https://github.com/milvus-io/milvus/pull/33014">#33014</a>)</li>
<li>빈로그의 메모리 데이터 크기를 추적하는 기능 추가<a href="https://github.com/milvus-io/milvus/pull/33025">(#33025</a>).</li>
<li>세그먼트 인덱스 파일 크기에 대한 메트릭 추가<a href="https://github.com/milvus-io/milvus/pull/32979">(#32979</a>, <a href="https://github.com/milvus-io/milvus/pull/33305">#33305</a>).</li>
<li>메트릭을 제거하기 위해 Delete를 DeletePartialMatch로 대체<a href="https://github.com/milvus-io/milvus/pull/33029">(#33029</a>).</li>
<li>세그먼트 유형에 따른 관련 데이터 크기 확보<a href="https://github.com/milvus-io/milvus/pull/33017">(#33017</a>)</li>
<li>메타 스토어에서 채널 노드 정보 정리<a href="https://github.com/milvus-io/milvus/pull/32988">(#32988</a>)</li>
<li>데이터노드 브로커에서 루트코드 제거<a href="https://github.com/milvus-io/milvus/pull/32818">(#32818</a>)</li>
<li>일괄 업로드 활성화<a href="https://github.com/milvus-io/milvus/pull/32788">(#32788</a>)</li>
<li>파티션 키 사용 시 기본 파티션 번호를 16으로 변경<a href="https://github.com/milvus-io/milvus/pull/32950">(#32950</a>).</li>
<li>매우 큰 상위 k 쿼리에서 성능 저하 개선<a href="https://github.com/milvus-io/milvus/pull/32871">(#32871</a>)</li>
<li>쓰기 및 압축을 가속화하기 위해 TestLocations 기능 활용<a href="https://github.com/milvus-io/milvus/pull/32948">(#32948</a>)</li>
<li>불필요한 재활용을 피하기 위해 최적화된 계획 파서 풀<a href="https://github.com/milvus-io/milvus/pull/32869">(#32869</a>)</li>
<li>로드 속도 개선<a href="https://github.com/milvus-io/milvus/pull/32898">(#32898</a>)</li>
<li>restv2에 대해 수집 기본 일관성 수준 사용<a href="https://github.com/milvus-io/milvus/pull/32956">(#32956</a>)</li>
<li>rest API에 대한 비용 응답 추가<a href="https://github.com/milvus-io/milvus/pull/32620">(#32620</a>)</li>
<li>채널 전용 잔액 정책 활성화<a href="https://github.com/milvus-io/milvus/pull/32911">(#32911</a>)</li>
<li>프록시에 설명된 데이터베이스 API 노출<a href="https://github.com/milvus-io/milvus/pull/32732">(#32732</a>)</li>
<li>컬렉션별로 RG를 가져올 때 coll2replica 매핑 활용<a href="https://github.com/milvus-io/milvus/pull/32892">(#32892</a>)</li>
<li>검색 및 쿼리에 대한 추적 기능 추가<a href="https://github.com/milvus-io/milvus/pull/32734">(#32734</a>)</li>
<li>오픈 텔레메트리 추적을 위한 동적 구성 지원<a href="https://github.com/milvus-io/milvus/pull/32169">(#32169</a>)</li>
<li>리더뷰 업데이트 시 채널 결과에 대한 반복 방지<a href="https://github.com/milvus-io/milvus/pull/32887">(#32887</a>)</li>
<li>쪽모이 세공에 대한 벡터 오프셋 처리 최적화<a href="https://github.com/milvus-io/milvus/pull/32822">(#32822</a>)</li>
<li>수집 시 데이터코드 세그먼트 필터링 개선<a href="https://github.com/milvus-io/milvus/pull/32831">(#32831</a>)</li>
<li>로그 수준 및 빈도 조정<a href="https://github.com/milvus-io/milvus/pull/33042">(#33042</a>, <a href="https://github.com/milvus-io/milvus/pull/32838">#32838</a>, <a href="https://github.com/milvus-io/milvus/pull/33337">#33337</a>)</li>
<li>잔액 정지 후 잔액 중지 활성화<a href="https://github.com/milvus-io/milvus/pull/32812">(#32812</a>)</li>
<li>리더 위치 변경 시 샤드 리더 캐시 업데이트<a href="https://github.com/milvus-io/milvus/pull/32470">(#32470</a>)</li>
<li>더 이상 사용되지 않는 API 및 필드 제거<a href="https://github.com/milvus-io/milvus/pull/32808">(#32808</a>, <a href="https://github.com/milvus-io/milvus/pull/32704">#32704</a>).</li>
<li>문자열 비교를 int로 변환하는 metautil.channel 추가<a href="https://github.com/milvus-io/milvus/pull/32749">(#32749</a>).</li>
<li>쿼리노드가 새 컬렉션을 발견했을 때 페이로드 작성기 오류 메시지 및 로그에 대한 유형 정보 추가<a href="https://github.com/milvus-io/milvus/pull/32522">(#32522</a>).</li>
<li>파티션 키로 컬렉션 생성 시 파티션 번호 확인<a href="https://github.com/milvus-io/milvus/pull/32670">(#32670</a>).</li>
<li>감시 실패 시 레거시 l0 세그먼트 제거<a href="https://github.com/milvus-io/milvus/pull/32725">(#32725</a>)</li>
<li>요청 인쇄 유형 개선<a href="https://github.com/milvus-io/milvus/pull/33319">(#33319</a>)</li>
<li>유형을 가져오기 전에 배열 필드 데이터가 nil인지 확인<a href="https://github.com/milvus-io/milvus/pull/33311">(#33311</a>).</li>
<li>스타트업 삭제/추가 노드 작업 실패 시 오류 반환<a href="https://github.com/milvus-io/milvus/pull/33258">(#33258</a>)</li>
<li>데이터 노드의 서버 ID 업데이트 허용<a href="https://github.com/milvus-io/milvus/pull/31597">(#31597</a>)</li>
<li>컬렉션 릴리즈에서 통합 쿼리 노드 메트릭 정리<a href="https://github.com/milvus-io/milvus/pull/32805">(#32805</a>)</li>
<li>스칼라 자동 인덱스 구성의 잘못된 버전 수정<a href="https://github.com/milvus-io/milvus/pull/32795">(#32795</a>)</li>
<li>인덱스 생성/변경 시 인덱스 매개변수 검사 개선<a href="https://github.com/milvus-io/milvus/pull/32712">(#32712</a>)</li>
<li>중복 복제본 복구 제거<a href="https://github.com/milvus-io/milvus/pull/32985">(#32985</a>)</li>
<li>채널 메타 테이블에서 200만 개 이상의 세그먼트 쓰기 활성화<a href="https://github.com/milvus-io/milvus/pull/33300">(#33300</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">버그 수정</h3><ul>
<li>속도 제한 인터셉터에 데이터베이스가 존재하지 않을 때 발생하는 패닉 수정<a href="https://github.com/milvus-io/milvus/pull/33308">(#33308</a>)</li>
<li>잘못된 매개변수로 인한 쿼터 센터 메트릭 수집 실패 수정<a href="https://github.com/milvus-io/milvus/pull/33399">(#33399</a>)</li>
<li>프로세스 활성화 대기 중 오류가 반환되면 패닉이 발생하는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/33372">(#33372</a>)</li>
<li>nq &gt; 1일 때 restful v2에서 검색 결과 잘림 현상 수정<a href="https://github.com/milvus-io/milvus/pull/33363">(#33363</a>).</li>
<li>restful v2에서 역할 작업에 대한 데이터베이스 이름 필드 추가<a href="https://github.com/milvus-io/milvus/pull/33291">(#33291</a>)</li>
<li>글로벌 속도 제한이 작동하지 않는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/33336">(#33336</a>)</li>
<li>인덱스 구축 실패로 인한 패닉 수정<a href="https://github.com/milvus-io/milvus/pull/33314">(#33314</a>)</li>
<li>합법성을 보장하기 위해 세그코어의 스파스 벡터에 대한 유효성 검사 추가<a href="https://github.com/milvus-io/milvus/pull/33312">(#33312</a>).</li>
<li>작업 완료 후 syncmgr에서 작업 제거<a href="https://github.com/milvus-io/milvus/pull/33303">(#33303</a>)</li>
<li>데이터 가져오기 중 파티션 키 필터링 실패 수정<a href="https://github.com/milvus-io/milvus/pull/33277">(#33277</a>)</li>
<li>noop 내보내기 사용 시 traceID를 생성할 수 없는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/33208">(#33208</a>)</li>
<li>쿼리 결과 검색 개선<a href="https://github.com/milvus-io/milvus/pull/33179">(#33179</a>)</li>
<li>체크포인트 지연 메트릭 누출을 방지하기 위해 채널 체크포인트 삭제 표시<a href="https://github.com/milvus-io/milvus/pull/33201">(#33201</a>)</li>
<li>진행 중지 중 쿼리 노드가 멈추는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/33154">(#33154</a>)</li>
<li>플러시 응답에서 누락된 세그먼트 수정<a href="https://github.com/milvus-io/milvus/pull/33061">(#33061</a>)</li>
<li>제출 작업이 무력화되도록 수정<a href="https://github.com/milvus-io/milvus/pull/33053">(#33053</a>)</li>
<li>스트리밍 리더에서 각 배치에 새 슬라이스 할당<a href="https://github.com/milvus-io/milvus/pull/33360">(#33360</a>)</li>
<li>쿼리코드 재시작 후 리소스 그룹에서 오프라인 노드 정리<a href="https://github.com/milvus-io/milvus/pull/33233">(#33233</a>).</li>
<li>완료된 컴팩터에서 l0 컴팩터 제거<a href="https://github.com/milvus-io/milvus/pull/33216">(#33216</a>).</li>
<li>리미터 초기화 시 쿼터 값 재설정<a href="https://github.com/milvus-io/milvus/pull/33152">(#33152</a>)</li>
<li>etcd 한도가 초과되는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/33041">(#33041</a>)</li>
<li>너무 많은 필드로 인한 etcd 트랜잭션 한도 초과 문제 해결<a href="https://github.com/milvus-io/milvus/pull/33040">(#33040</a>)</li>
<li>GetNumRowsOfPartition에서 RLock 재진입 제거<a href="https://github.com/milvus-io/milvus/pull/33045">(#33045</a>).</li>
<li>리더 캐시 옵저버를 SyncAll보다 먼저 시작<a href="https://github.com/milvus-io/milvus/pull/33035">(#33035</a>).</li>
<li>해제된 대기 채널의 밸런싱 활성화<a href="https://github.com/milvus-io/milvus/pull/32986">(#32986</a>)</li>
<li>서버 초기화 전에 액세스 로거 초기화<a href="https://github.com/milvus-io/milvus/pull/32976">(#32976</a>)</li>
<li>빈 세그먼트를 지울 수 있는 컴팩터를 만들었습니다<a href="https://github.com/milvus-io/milvus/pull/32821">(#32821</a>).</li>
<li>l0 압축에서 채워진 델타로그 항목 번호 및 시간 범위<a href="https://github.com/milvus-io/milvus/pull/33004">(#33004</a>)</li>
<li>샤드 리더 캐시 데이터 경쟁으로 인한 프록시 크래시 수정<a href="https://github.com/milvus-io/milvus/pull/32971">(#32971</a>).</li>
<li>로드 인덱스 메트릭의 시간 단위 수정<a href="https://github.com/milvus-io/milvus/pull/32935">(#32935</a>)</li>
<li>쿼리 노드 중지 시 세그먼트를 성공적으로 해제할 수 없는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/32929">(#32929</a>).</li>
<li>인덱스 리소스 추정 수정<a href="https://github.com/milvus-io/milvus/pull/32842">(#32842</a>)</li>
<li>채널 체크포인트를 델타 위치로 설정<a href="https://github.com/milvus-io/milvus/pull/32878">(#32878</a>)</li>
<li>미래를 반환하기 전에 syncmgr 잠금 키를 만들었습니다<a href="https://github.com/milvus-io/milvus/pull/32865">(#32865</a>).</li>
<li>반전된 인덱스에 세그먼트가 하나만 있는지 확인<a href="https://github.com/milvus-io/milvus/pull/32858">(#32858</a>)</li>
<li>압축 트리거가 두 개의 동일한 세그먼트를 선택하는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/32800">(#32800</a>)</li>
<li>빈로그 가져오기에서 파티션 이름을 지정할 수 없는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/32730">(#32730</a>, <a href="https://github.com/milvus-io/milvus/pull/33027">#33027</a>).</li>
<li>쪽모이 세공 가져오기에서 동적 열을 옵션으로 설정<a href="https://github.com/milvus-io/milvus/pull/32738">(#32738</a>).</li>
<li>데이터 삽입 시 자동 ID 확인 생략<a href="https://github.com/milvus-io/milvus/pull/32775">(#32775</a>)</li>
<li>스키마가 있는 필드 데이터 삽입 시 행 수 검증<a href="https://github.com/milvus-io/milvus/pull/32770">(#32770</a>)</li>
<li>CTraceContext ID에 대한 래퍼 및 킵얼라이브 추가<a href="https://github.com/milvus-io/milvus/pull/32746">(#32746</a>)</li>
<li>데이터코드 메타 객체에서 데이터베이스 이름을 찾을 수 없는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/33412">(#33412</a>)</li>
<li>삭제된 파티션에 대해 동기화된 삭제된 세그먼트<a href="https://github.com/milvus-io/milvus/pull/33332">(#33332</a>)</li>
<li>잘못된 매개 변수로 인한 쿼타 센터 메트릭 수집 실패 수정<a href="https://github.com/milvus-io/milvus/pull/33399">(#33399</a>)</li>
</ul>
<h2 id="v241" class="common-anchor-header">v2.4.1<button data-href="#v241" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜: 2024년 5월 6일</p>
<table>
<thead>
<tr><th>Milvus 버전</th><th>Python SDK 버전</th><th>Java SDK 버전</th><th>Node.js SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.1</td><td>2.4.1</td><td>2.4.0</td><td>2.4.2</td></tr>
</tbody>
</table>
<p>Milvus 버전 2.4.1은 소프트웨어의 성능, 통합 가시성 및 안정성을 향상시키기 위한 다양한 개선 사항과 버그 수정을 제공합니다. 이러한 개선 사항에는 선언적 리소스 그룹 API, Float16/BFloat16 벡터 데이터 유형을 지원하는 향상된 대량 삽입 기능, 객체 스토리지의 목록 작업을 줄여주는 개선된 가비지 컬렉션(GC) 메커니즘, 성능 최적화와 관련된 기타 변경 사항 등이 포함됩니다. 또한 컴파일 오류, 줄 바꿈 문자에 대한 퍼지 일치 실패, RESTful 인터페이스의 잘못된 매개변수 데이터 유형, 동적 필드가 활성화된 경우 numpy 파일에서 오류가 발생하는 BulkInsert 등의 문제를 해결하는 버그 수정이 이루어졌습니다.</p>
<h3 id="Breaking-changes" class="common-anchor-header">중단 변경 사항</h3><ul>
<li>빈 필터 표현식을 사용한 삭제에 대한 지원이 중단되었습니다.<a href="https://github.com/milvus-io/milvus/pull/32472">(#32472</a>)</li>
</ul>
<h3 id="Features" class="common-anchor-header">기능</h3><ul>
<li>대량 삽입에서 Float16/BFloat16 벡터 데이터 유형에 대한 지원 추가<a href="https://github.com/milvus-io/milvus/pull/32157">(#32157</a>)</li>
<li>무차별 반복자 검색 및 범위 검색을 지원하도록 스파스 플로트 벡터가 개선되었습니다<a href="https://github.com/milvus-io/milvus/pull/32635">(#32635</a>).</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">개선 사항</h3><ul>
<li>선언적 리소스 그룹 API 추가<a href="https://github.com/milvus-io/milvus/pull/31930">(#31930</a>, <a href="https://github.com/milvus-io/milvus/pull/32297">#32297</a>, <a href="https://github.com/milvus-io/milvus/pull/32536">#32536</a>, <a href="https://github.com/milvus-io/milvus/pull/32666">#32666</a>).</li>
<li>쿼리코드에서 컬렉션 옵저버를 작업 중심으로 재작성<a href="https://github.com/milvus-io/milvus/pull/32441">(#32441</a>).</li>
<li>메모리 사용량을 줄이고 오류를 방지하기 위해 DataNode의 SyncManager에서 사용되는 데이터 구조를 리팩터링<a href="https://github.com/milvus-io/milvus/pull/32673">(#32673</a>).</li>
<li>가비지 컬렉션 구현을 수정하여 오브젝트 스토리지와 관련된 목록 연산을 최소화<a href="https://github.com/milvus-io/milvus/pull/31740">(#31740</a>).</li>
<li>수집 수가 많을 때 CPU 사용량 감소<a href="https://github.com/milvus-io/milvus/pull/32245">(#32245</a>)</li>
<li>코드를 통해 milvus.yaml 파일에 관련 구성 항목을 자동으로 생성하여 milvus.yaml 관리 개선<a href="https://github.com/milvus-io/milvus/pull/31832">(#31832</a>, <a href="https://github.com/milvus-io/milvus/pull/32357">#32357</a>).</li>
<li>로컬 축소를 수행한 후 데이터를 검색하여 쿼리 성능을 향상시켰습니다<a href="https://github.com/milvus-io/milvus/pull/32346">(#32346</a>).</li>
<li>etcd 클라이언트 생성에 WithBlock 옵션 추가<a href="https://github.com/milvus-io/milvus/pull/32641">(#32641</a>)</li>
<li>클라이언트가 제공한 경우 클라이언트가 지정한 client_request_id를 TraceID로 사용<a href="https://github.com/milvus-io/milvus/pull/32264">(#32264</a>).</li>
<li>삭제 및 대량 삽입 작업의 메트릭에 db 레이블 추가<a href="https://github.com/milvus-io/milvus/pull/32611">(#32611</a>).</li>
<li>AutoID 및 PartitionKey 열에 대한 구성을 통해 확인을 건너뛰는 로직 추가<a href="https://github.com/milvus-io/milvus/pull/32592">(#32592</a>).</li>
<li>인증 관련 오류 개선<a href="https://github.com/milvus-io/milvus/pull/32253">(#32253</a>)</li>
<li>DataCoord에서 AllocSegmentID에 대한 오류 로그 개선<a href="https://github.com/milvus-io/milvus/pull/32351">(#32351</a>, <a href="https://github.com/milvus-io/milvus/pull/32335">#32335</a>)</li>
<li>중복 메트릭 제거<a href="https://github.com/milvus-io/milvus/pull/32380">(#32380</a>, <a href="https://github.com/milvus-io/milvus/pull/32308">#32308</a>) 및 사용되지 않는 메트릭 정리<a href="https://github.com/milvus-io/milvus/pull/32404">(#32404</a>, <a href="https://github.com/milvus-io/milvus/pull/32515">#32515</a>).</li>
<li>partitionKey 기능의 활성화 여부를 제어하는 구성 옵션 추가<a href="https://github.com/milvus-io/milvus/pull/32433">(#32433</a>).</li>
<li>단일 요청에 삽입할 수 있는 최대 데이터 양을 제어하는 구성 옵션 추가<a href="https://github.com/milvus-io/milvus/pull/32433">(#32433</a>).</li>
<li>세그먼트 수준에서 적용/삭제 작업을 병렬화하여 위임자에 의한 삭제 메시지 처리 가속화<a href="https://github.com/milvus-io/milvus/pull/32291">(#32291</a>).</li>
<li>인덱스<a href="https://github.com/milvus-io/milvus/pull/32232">(#32232</a>, <a href="https://github.com/milvus-io/milvus/pull/32505">#32505</a>, <a href="https://github.com/milvus-io/milvus/pull/32533">#32533</a>, <a href="https://github.com/milvus-io/milvus/pull/32595">#32595</a>)를 사용하고 캐시<a href="https://github.com/milvus-io/milvus/pull/32580">(#32580</a>)를 추가하여 QueryCoord에서 빈번한 필터링 작업을 가속화합니다.</li>
<li>데이터 구조를 재작성<a href="https://github.com/milvus-io/milvus/pull/32273">(#32273</a>)하고 코드를 리팩터링<a href="https://github.com/milvus-io/milvus/pull/32389">(#32389</a>)하여 DataCoord에서 일반적인 작업을 가속화했습니다.</li>
<li>코난에서 오픈블라스를 제거했습니다<a href="https://github.com/milvus-io/milvus/pull/32002">(#32002</a>).</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">버그 수정</h3><ul>
<li>rockylinux8에서 빌드 밀버스 수정<a href="https://github.com/milvus-io/milvus/pull/32619">(#32619</a>)</li>
<li>ARM에서 SVE의 컴파일 오류 수정<a href="https://github.com/milvus-io/milvus/pull/32463">(#32463</a>, <a href="https://github.com/milvus-io/milvus/pull/32270">#32270</a>)</li>
<li>ARM 기반 GPU 이미지에서 충돌 문제 수정<a href="https://github.com/milvus-io/milvus/pull/31980">(#31980</a>).</li>
<li>정규식 쿼리가 개행이 있는 텍스트를 처리할 수 없는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/32569">(#32569</a>)</li>
<li>GetShardLeaders가 빈 노드 목록을 반환하여 검색 결과가 비어 있는 문제를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/32685">(#32685</a>).</li>
<li>numpy 파일에서 동적 필드를 만나면 BulkInsert가 오류를 발생시키는 문제를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/32596">(#32596</a>).</li>
<li>요청의 숫자 매개변수가 문자열 유형 대신 숫자 입력을 허용하도록 하는 중요한 수정<a href="https://github.com/milvus-io/milvus/pull/32485">(#32485</a>, <a href="https://github.com/milvus-io/milvus/pull/32355">#32355</a>)을 포함하여 RESTFulV2 인터페이스와 관련된 버그가 수정되었습니다.</li>
<li>전송률 제한기에서 구성 이벤트 감시를 제거하여 프록시에서 메모리 누수를 수정했습니다<a href="https://github.com/milvus-io/milvus/pull/32313">(#32313</a>).</li>
<li>파티션 이름이 지정되지 않은 경우 속도 제한기가 파티션을 찾을 수 없다고 잘못 보고하는 문제 수정<a href="https://github.com/milvus-io/milvus/pull/32647">(#32647</a>)</li>
<li>오류 유형에 컬렉션이 복구 상태인 경우와 로드되지 않은 경우 사이에 감지 기능을 추가했습니다.<a href="https://github.com/milvus-io/milvus/pull/32447">(#32447</a>)</li>
<li>음수 쿼리 가능 엔티티 수 메트릭 수정<a href="https://github.com/milvus-io/milvus/pull/32361">(#32361</a>)</li>
</ul>
<h2 id="v240" class="common-anchor-header">v2.4.0<button data-href="#v240" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜: 2024년 4월 17일</p>
<table>
<thead>
<tr><th>Milvus 버전</th><th>Python SDK 버전</th><th>Node.js SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.0</td><td>2.4.0</td><td>2.4.0</td></tr>
</tbody>
</table>
<p>2.4.0-rc.1 릴리스의 견고한 기반을 바탕으로 기존 기능을 유지하면서 사용자가 보고한 중요한 버그를 해결하는 데 중점을 두어 Milvus 2.4.를 공식 출시하게 되어 기쁘게 생각합니다. 또한 Milvus 2.4.0은 시스템 성능 향상, 다양한 메트릭 통합을 통한 관찰 가능성 개선, 코드베이스 간소화를 위한 다양한 최적화를 도입하여 단순성을 높였습니다.</p>
<h3 id="Improvements" class="common-anchor-header">개선 사항</h3><ul>
<li>MinIO TLS 연결 지원<a href="https://github.com/milvus-io/milvus/pull/31396">(#31396</a>, <a href="https://github.com/milvus-io/milvus/pull/31618">#31618</a>)</li>
<li>스칼라 필드에 대한 자동 색인 지원<a href="https://github.com/milvus-io/milvus/pull/31593">(#31593</a>)</li>
<li>일반 검색과 일관된 실행 경로를 위한 하이브리드 검색 리팩터링<a href="https://github.com/milvus-io/milvus/pull/31742">(#31742</a>, <a href="https://github.com/milvus-io/milvus/pull/32178">#32178</a>)</li>
<li>bitset 및 bitset_view 리팩터링을 통한 필터링 가속화<a href="https://github.com/milvus-io/milvus/pull/31592">(#31592</a>, <a href="https://github.com/milvus-io/milvus/pull/31754">#31754</a>, <a href="https://github.com/milvus-io/milvus/pull/32139">#32139</a>).</li>
<li>가져오기 작업에서 이제 데이터 인덱스 완료 대기 지원<a href="https://github.com/milvus-io/milvus/pull/31733">(#31733</a>)</li>
<li>가져오기 호환성<a href="https://github.com/milvus-io/milvus/pull/32121">(#32121</a>), 작업 예약<a href="https://github.com/milvus-io/milvus/pull/31475">(#31475)</a>, 가져오기 파일 크기 및 수 제한<a href="https://github.com/milvus-io/milvus/pull/31542">(#31542</a>)이 향상되었습니다.</li>
<li>유형 검사를 위한 인터페이스 표준화<a href="https://github.com/milvus-io/milvus/pull/31945">(#31945</a>, <a href="https://github.com/milvus-io/milvus/pull/31857">#31857</a>), 더 이상 사용되지 않는 코드 및 메트릭 제거<a href="https://github.com/milvus-io/milvus/pull/32079">(#32079</a>, <a href="https://github.com/milvus-io/milvus/pull/32134">#32134</a>, <a href="https://github.com/milvus-io/milvus/pull/31535">#31535</a>, <a href="https://github.com/milvus-io/milvus/pull/32211">#32211,</a> <a href="https://github.com/milvus-io/milvus/pull/31935">#31935</a>), 상수 이름 정규화<a href="https://github.com/milvus-io/milvus/pull/31515">(#31515</a>) 등 코드 간소화 노력</li>
<li>쿼리코드 현재 목표 채널 체크포인트 지연 대기 시간에 대한 새로운 메트릭<a href="https://github.com/milvus-io/milvus/pull/31420">(#31420</a>)</li>
<li>공통 메트릭에 대한 새로운 DB 레이블<a href="https://github.com/milvus-io/milvus/pull/32024">(#32024</a>)</li>
<li>삭제, 색인 및 로드된 엔티티의 수에 관한 새로운 메트릭, 컬렉션 이름 및 dbName과 같은 레이블 포함<a href="https://github.com/milvus-io/milvus/pull/31861">(#31861</a>).</li>
<li>일치하지 않는 벡터 유형에 대한 오류 처리 개선<a href="https://github.com/milvus-io/milvus/pull/31766">(#31766</a>)</li>
<li>인덱스를 빌드할 수 없을 때 크래시 대신 오류 발생 지원<a href="https://github.com/milvus-io/milvus/pull/31845">(#31845</a>)</li>
<li>데이터베이스를 삭제할 때 데이터베이스 메타 캐시 무효화 지원<a href="https://github.com/milvus-io/milvus/pull/32092">(#32092</a>)</li>
<li>채널 배포<a href="https://github.com/milvus-io/milvus/pull/31814">(#31814</a>) 및 리더 뷰 관리<a href="https://github.com/milvus-io/milvus/pull/32127">(#32127</a>)를 위한 인터페이스 리팩터링<a href="https://github.com/milvus-io/milvus/pull/31814">(#31814</a>)</li>
<li>채널 배포 관리자 인터페이스 리팩터링<a href="https://github.com/milvus-io/milvus/pull/31814">(#31814</a>) 및 리더 뷰 관리자 인터페이스 리팩터링<a href="https://github.com/milvus-io/milvus/pull/32127">(#32127</a>)</li>
<li>일괄 처리<a href="https://github.com/milvus-io/milvus/pull/31632">(#31632</a>), 매핑 정보 추가<a href="https://github.com/milvus-io/milvus/pull/32234">(#32234</a>, <a href="https://github.com/milvus-io/milvus/pull/32249">#32249</a>), 자주 호출되는 작업 가속화를 위한 잠금 사용 방지<a href="https://github.com/milvus-io/milvus/pull/31787">(#31787</a>)</li>
</ul>
<h3 id="Breaking-Changes" class="common-anchor-header">중단 변경 사항</h3><ul>
<li>이진 벡터에서 그룹화 검색 중단<a href="https://github.com/milvus-io/milvus/pull/31735">(#31735</a>)</li>
<li>하이브리드 검색을 사용한 그룹화 검색 중단<a href="https://github.com/milvus-io/milvus/pull/31812">(#31812</a>)</li>
<li>바이너리 벡터에서 HNSW 인덱스 사용 중단<a href="https://github.com/milvus-io/milvus/pull/31883">(#31883</a>)</li>
</ul>
<h3 id="Bug-Fixes" class="common-anchor-header">버그 수정</h3><ul>
<li>충돌을 방지하기 위해 쿼리 및 삽입에 대한 데이터 유형 및 값 검사 강화<a href="https://github.com/milvus-io/milvus/pull/31478">(#31478</a>, <a href="https://github.com/milvus-io/milvus/pull/31653">#31653</a>, <a href="https://github.com/milvus-io/milvus/pull/31698">#31698</a>, <a href="https://github.com/milvus-io/milvus/pull/31842">#31842</a>, <a href="https://github.com/milvus-io/milvus/pull/32042">#32042</a>, <a href="https://github.com/milvus-io/milvus/pull/32251">#32251</a>, <a href="https://github.com/milvus-io/milvus/pull/32204">#32204</a>)</li>
<li>RESTful API 버그 수정<a href="https://github.com/milvus-io/milvus/pull/32160">(#32160</a>)</li>
<li>역 인덱스 리소스 사용량 예측 개선<a href="https://github.com/milvus-io/milvus/pull/31641">(#31641</a>)</li>
<li>권한 부여가 활성화된 경우 etcd와의 연결 문제 해결<a href="https://github.com/milvus-io/milvus/pull/31668">(#31668</a>)</li>
<li>nats 서버에 대한 보안 업데이트<a href="https://github.com/milvus-io/milvus/pull/32023">(#32023</a>)</li>
<li>반전된 인덱스 파일을 /tmp가 아닌 QueryNode의 로컬 저장 경로에 저장<a href="https://github.com/milvus-io/milvus/pull/32210">(#32210</a>)</li>
<li>collectionInfo의 데이터코드 메모리 누수 문제 해결<a href="https://github.com/milvus-io/milvus/pull/32243">(#32243</a>)</li>
<li>시스템 패닉을 일으킬 수 있는 fp16/bf16 관련 버그 수정<a href="https://github.com/milvus-io/milvus/pull/31677">(#31677</a>, <a href="https://github.com/milvus-io/milvus/pull/31841">#31841</a>, <a href="https://github.com/milvus-io/milvus/pull/32196">#32196</a>).</li>
<li>그룹 검색이 불충분한 결과를 반환하는 문제 해결<a href="https://github.com/milvus-io/milvus/pull/32151">(#32151</a>)</li>
<li>Reduce 단계에서 오프셋을 보다 효과적으로 처리하고 'reduceStopForBest'가 활성화된 상태에서 적절한 결과를 보장하기 위해 반복기를 사용한 검색 조정<a href="https://github.com/milvus-io/milvus/pull/32088">(#32088</a>).</li>
</ul>
<h2 id="v240-rc1" class="common-anchor-header">v2.4.0-rc.1<button data-href="#v240-rc1" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>릴리스 날짜: 2024년 3월 20일</p>
<table>
<thead>
<tr><th>Milvus 버전</th><th>Python SDK 버전</th></tr>
</thead>
<tbody>
<tr><td>2.4.0-rc.1</td><td>2.4.0</td></tr>
</tbody>
</table>
<p>이번 릴리스에는 몇 가지 시나리오 기반 기능이 도입되었습니다:</p>
<ul>
<li><p><strong>새로운 GPU 인덱스 - CAGRA</strong>: NVIDIA의 기여 덕분에 이 새로운 GPU 인덱스는 특히 일괄 검색에서 10배의 성능 향상을 제공합니다. 자세한 내용은 <a href="/docs/ko/gpu_index.md">GPU 인덱스를</a> 참조하세요.</p></li>
<li><p><strong>멀티 벡터</strong> 및 <strong>하이브리드 검색</strong>: 이 기능을 사용하면 여러 모델의 벡터 임베딩을 저장하고 하이브리드 검색을 수행할 수 있습니다. 자세한 내용은 <a href="/docs/ko/multi-vector-search.md">하이브리드 검색을</a> 참조하세요.</p></li>
<li><p><strong>스파스 벡터</strong>: 키워드 해석 및 분석에 이상적인 스파스 벡터는 이제 컬렉션에서 처리할 수 있도록 지원됩니다. 자세한 내용은 <a href="/docs/ko/sparse_vector.md">스파스 벡터를</a> 참조하세요.</p></li>
<li><p><strong>검색 그룹화</strong>: 범주형 집계는 검색 증강 생성(RAG) 애플리케이션의 문서 수준 검색을 향상시킵니다. 자세한 내용은 <a href="https://milvus.io/docs/single-vector-search.md#Grouping-search">그룹화 검색을</a> 참조하세요.</p></li>
<li><p><strong>반전 인덱스</strong> 및 <strong>퍼지 매칭</strong>: 이 기능은 스칼라 필드에 대한 키워드 검색을 개선합니다. 자세한 내용은 <a href="/docs/ko/index-scalar-fields.md">스칼라 필드 색인</a> 및 <a href="/docs/ko/single-vector-search.md#filtered-search">필터링된 검색을</a> 참조하세요.</p></li>
</ul>
<h3 id="New-Features" class="common-anchor-header">새로운 기능</h3><h4 id="GPU-Index---CAGRA" class="common-anchor-header">GPU 색인 - CAGRA</h4><p>온라인에서 사용할 수 있는 최신(SoTA) GPU 기반 그래프 인덱스인 CAGRA에 귀중한 기여를 해주신 NVIDIA 팀에 진심으로 감사드립니다.</p>
<p>이전 GPU 인덱스와 달리 CAGRA는 전통적으로 CPU 인덱스가 뛰어난 영역인 소규모 배치 쿼리에서도 압도적인 우월성을 보여줍니다. 또한, GPU 인덱스가 이미 강세를 보이고 있는 영역인 대규모 배치 쿼리 및 인덱스 구축 속도에서 CAGRA의 성능은 정말 타의 추종을 불허합니다.</p>
<p>예제 코드는 <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/example_gpu_cagra.py">example_gpu_cagra.py에서</a> 확인할 수 있습니다.</p>
<h4 id="Sparse-Vector-Beta" class="common-anchor-header">스파스 벡터(베타)</h4><p>이번 릴리스에서는 스파스 벡터라는 새로운 유형의 벡터 필드를 도입합니다. 스파스 벡터는 밀도가 높은 벡터와 달리 차원 수가 몇 배 더 많으며 소수만 0이 아닌 경향이 있습니다. 이 기능은 용어 기반의 특성으로 인해 더 나은 해석 가능성을 제공하며 특정 도메인에서 더 효과적일 수 있습니다. SPLADEv2/BGE-M3와 같은 학습된 희소 모델은 일반적인 1단계 랭킹 작업에 매우 유용하다는 것이 입증되었습니다. Milvus의 이 새로운 기능의 주요 사용 사례는 SPLADEv2/BGE-M3와 같은 신경 모델과 BM25 알고리즘과 같은 통계 모델에 의해 생성된 희소 벡터에 대해 효율적인 근사 의미론적 최인접 이웃 검색을 가능하게 하는 것입니다. 밀버스는 이제 희소 벡터의 효과적인 고성능 저장, 인덱싱, 검색(MIPS, 최대 내부 제품 검색)을 지원합니다.</p>
<p>예제 코드는 <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/hello_sparse.py">hello_sparse.py에서</a> 확인할 수 있습니다.</p>
<h4 id="Multi-Embedding---Hybrid-Search" class="common-anchor-header">멀티 임베딩 및 하이브리드 검색</h4><p>다중 벡터 지원은 다중 모델 데이터 처리 또는 고밀도 벡터와 희소 벡터의 혼합이 필요한 애플리케이션을 위한 초석입니다. 이제 멀티 벡터 지원으로 가능합니다:</p>
<ul>
<li>여러 모델에서 비정형 텍스트, 이미지 또는 오디오 샘플을 위해 생성된 벡터 임베딩을 저장할 수 있습니다.</li>
<li>각 엔티티의 여러 벡터를 포함하는 ANN 검색을 수행합니다.</li>
<li>다양한 임베딩 모델에 가중치를 할당하여 검색 전략을 사용자 정의합니다.</li>
<li>다양한 임베딩 모델을 실험하여 최적의 모델 조합을 찾을 수 있습니다.</li>
</ul>
<p>다중 벡터를 지원하므로 컬렉션에 FLOAT_VECTOR, SPARSE_FLOAT_VECTOR와 같은 다양한 유형의 여러 벡터 필드를 저장, 인덱싱하고 재랭크 전략을 적용할 수 있습니다. 현재 두 가지 재랭크 전략을 사용할 수 있습니다: <strong>상호 순위 융합(RRF)</strong> 과 <strong>평균 가중치 점수입니다</strong>. 두 전략 모두 서로 다른 벡터 필드의 검색 결과를 통합된 결과 집합으로 결합합니다. 첫 번째 전략은 서로 다른 벡터 필드의 검색 결과에 일관되게 나타나는 엔티티에 우선순위를 부여하고, 다른 전략은 각 벡터 필드의 검색 결과에 가중치를 할당하여 최종 결과 집합에서 그 중요도를 결정합니다.</p>
<p>예제 코드는 <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/hybrid_search.py">hybrid_search.py에서</a> 찾을 수 있습니다.</p>
<h4 id="Inverted-Index-and-Fuzzy-Match" class="common-anchor-header">반전 인덱스 및 퍼지 일치</h4><p>이전 Milvus 릴리즈에서는 메모리 기반 이진 검색 인덱스와 마리사 트리 인덱스가 스칼라 필드 인덱싱에 사용되었습니다. 그러나 이러한 방법은 메모리 집약적이었습니다. 최신 Milvus 릴리즈는 이제 모든 숫자 및 문자열 데이터 유형에 적용할 수 있는 Tantivy 기반 반전 인덱스를 사용합니다. 이 새로운 인덱스는 스칼라 쿼리 성능을 획기적으로 개선하여 문자열 키워드 쿼리를 10배까지 줄여줍니다. 또한, 반전 인덱스는 데이터 압축과 내부 인덱싱 구조의 메모리 맵 저장(MMap) 메커니즘의 추가 최적화를 통해 메모리를 덜 소비합니다.</p>
<p>이번 릴리즈에서는 접두사, 접두사, 접미사를 사용한 스칼라 필터링에서 퍼지 매칭도 지원합니다.</p>
<p>예제 코드는 <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/inverted_index_example.py">inverted_index_example.py와</a> <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/fuzzy_match.py">fuzzy_match.py에서</a> 찾을 수 있습니다.</p>
<h4 id="Grouping-Search" class="common-anchor-header">검색 그룹화</h4><p>이제 특정 스칼라 필드의 값을 기준으로 검색 결과를 집계할 수 있습니다. 이는 RAG 애플리케이션이 문서 수준 리콜을 구현하는 데 도움이 됩니다. 각 문서가 여러 구절로 나뉘어져 있는 문서 모음을 생각해 봅시다. 각 구절은 하나의 벡터 임베딩으로 표현되며 하나의 문서에 속합니다. 구절이 흩어지는 대신 가장 관련성이 높은 문서를 찾으려면 search() 작업에 group_by_field 인수를 포함시켜 문서 ID를 기준으로 결과를 그룹화할 수 있습니다.</p>
<p>예제 코드는 <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/example_group_by.py">example_group_by.py에서</a> 찾을 수 있습니다.</p>
<h4 id="Float16-and-BFloat--Vector-DataType" class="common-anchor-header">Float16 및 BFloat- 벡터 데이터 유형</h4><p>머신 러닝과 신경망은 종종 Float16 및 BFloat와 같은 반정밀도 데이터 유형을 사용합니다. 이러한 데이터 유형은 쿼리 효율성을 개선하고 메모리 사용량을 줄일 수 있지만 정확도가 떨어진다는 단점이 있습니다. 이번 릴리스에서 Milvus는 이제 벡터 필드에 대해 이러한 데이터 유형을 지원합니다.</p>
<p>예제 코드는 <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/float16_example.py">float16_example.py</a> 및 <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/bfloat16_example.py">bfloat16_example.py에서</a> 확인할 수 있습니다.</p>
<h3 id="Upgraded-Architecture" class="common-anchor-header">업그레이드된 아키텍처</h3><h4 id="L0-Segment" class="common-anchor-header">L0 세그먼트</h4><p>이번 릴리스에는 삭제된 데이터를 기록하도록 설계된 L0 세그먼트라는 새로운 세그먼트가 포함되어 있습니다. 이 세그먼트는 저장된 삭제된 레코드를 주기적으로 압축하여 밀봉된 세그먼트로 분할함으로써 소규모 삭제에 필요한 데이터 플러시 횟수를 줄이고 저장 공간을 적게 차지합니다. 이 메커니즘을 통해 Milvus는 데이터 압축과 데이터 플러시를 완전히 분리하여 삭제 및 업서트 작업의 성능을 향상시킵니다.</p>
<h4 id="Refactored-BulkInsert" class="common-anchor-header">리팩터링된 대량 삽입</h4><p>이번 릴리스에는 향상된 대량 삽입 로직도 도입되었습니다. 이를 통해 한 번의 대량 삽입 요청으로 여러 파일을 가져올 수 있습니다. 리팩터링된 버전에서는 대량 삽입의 성능과 안정성이 모두 크게 개선되었습니다. 미세 조정된 속도 제한과 더욱 사용자 친화적인 오류 메시지 등 사용자 경험도 개선되었습니다. 또한 Milvus의 RESTful API를 통해 대량 삽입 엔드포인트에 쉽게 액세스할 수 있습니다.</p>
<h4 id="Memory-mapped-Storage" class="common-anchor-header">메모리 매핑 스토리지</h4><p>Milvus는 메모리 매핑 스토리지(MMap)를 사용하여 메모리 사용량을 최적화합니다. 이 메커니즘은 파일 콘텐츠를 메모리에 직접 로드하는 대신 파일 콘텐츠를 메모리에 매핑합니다. 이 접근 방식에는 성능 저하라는 트레이드오프가 있습니다.  CPU 2개와 8GB RAM이 있는 호스트에서 HNSW 색인 컬렉션에 MMap을 사용하도록 설정하면 10% 미만의 성능 저하로 4배 더 많은 데이터를 로드할 수 있습니다.</p>
<p>또한, 이번 릴리스에서는 Milvus를 다시 시작할 필요 없이 MMap을 동적이고 세밀하게 제어할 수 있습니다.</p>
<p>자세한 내용은 <a href="/docs/ko/mmap.md">MMap 스토리지를</a> 참조하세요.</p>
<h3 id="Others" class="common-anchor-header">기타</h3><h4 id="Milvus-CDC" class="common-anchor-header">Milvus-CDC</h4><p>Milvus-CDC는 Milvus 인스턴스 간에 증분 데이터를 캡처하고 동기화하여 손쉽게 증분 백업 및 재해 복구를 수행할 수 있는 사용하기 쉬운 동반 도구입니다. 이번 릴리스에서 Milvus-CDC는 안정성이 개선되었으며, 이제 변경 데이터 캡처(CDC) 기능을 일반적으로 사용할 수 있습니다.</p>
<p>Milvus-CDC에 대해 자세히 알아보려면 <a href="https://github.com/zilliztech/milvus-cdc">GitHub 리포지토리</a> 및 <a href="/docs/ko/milvus-cdc-overview.md">Milvus-CDC 개요를</a> 참조하세요.</p>
<h4 id="Refined-MilvusClient-Interfaces" class="common-anchor-header">개선된 MilvusClient 인터페이스</h4><p>MilvusClient는 ORM 모듈을 대체할 수 있는 사용하기 쉬운 인터페이스입니다. 서버와의 상호 작용을 단순화하기 위해 순전히 기능적인 접근 방식을 채택합니다. 연결 풀을 유지하는 대신 각 MilvusClient는 서버에 대한 gRPC 연결을 설정합니다. MilvusClient 모듈은 ORM 모듈의 대부분의 기능을 구현했습니다. MilvusClient 모듈에 대해 자세히 알아보려면 <a href="https://github.com/milvus-io/pymilvus">pymilvus</a> 및 <a href="/api-reference/pymilvus/v2.4.x/About.md">참조 문서를</a> 방문하세요.</p>

<script>
import _ from "lodash"
import moment from "moment"
import "moment/locale/ko"
import Button from "primevue/button"

moment.locale("ko")

export default {
  data() {
    return {
      now: new Date(),
      viewerMenu: [
        {
          title: "조업사 차량",
          items: [
            { name: "KAS", value: true },
            { name: "AAP", value: false },
            { name: "JAS", value: true },
            { name: "ATS", value: false },
            { name: "SAK", value: false },
            { name: "GAA", value: false },
          ],
        },
        {
          title: "구역보기",
          items: [
            { name: "탑승교 주의", value: true },
            { name: "항공기 주의", value: false },
            { name: "사고위험 주의", value: true },
            { name: "속도위반", value: false },
            { name: "저시정 구역", value: false },
            { name: "과속위험 지역", value: false },
          ],
        },
        {
          title: "항공기",
          items: [{ name: "위치 보이기 주의", value: true }],
        },
        {
          title: "위험지역",
          items: [
            { name: "과속 위험", value: true },
            { name: "사고 위험", value: true },
            { name: "기타 위험", value: true },
          ],
        },
        {
          title: "사고지역",
          items: [
            { name: "항공기 사고", value: true },
            { name: "차량 사고", value: true },
            { name: "시성물 사고", value: true },
          ],
        },
        {
          title: "항공기 점유율",
          items: [{ name: "점유율 보이기", value: true }],
        },
        {
          title: "항공기 경로",
          items: [{ name: "경로 보이기", value: true }],
        },
      ],
      countsData: [
        {
          title: "조업",
          color: "#2bc95c",
          count: 159,
        },
        {
          title: "주의",
          color: "#c9aa2b",
          count: 1,
        },
        {
          title: "위험",
          color: "#c98c2b",
          count: 5,
        },
        {
          title: "긴급",
          color: "#c9562b",
          count: 2,
        },
        {
          title: "사고",
          color: "#c92b2b",
          count: 1,
        },
      ],
      environmentData: [
        {
          caption: "2분평균",
          subject: "풍향/풍속",
          value: "200/4",
        },
        {
          caption: "좌측1분 평균",
          subject: "RVR",
          value: "P2000",
        },
        {
          caption: "좌측1분 평균",
          subject: "MOR",
          value: "10000",
        },
        {
          caption: "일산화탄소",
          subject: "1시간 평균",
          value: "1.9ppm",
        },
        {
          caption: "일산화탄소",
          subject: "24시간 평균",
          value: "0.8ppm",
        },
      ],
      environmentIssues: [
        {
          type: "긴급",
          color: "#c92b2b",
          port: "여수공항",
          content: "급변풍 (08.06 16 : 22~ 08.06 18:00 KST)",
        },
        {
          type: "긴급",
          color: "#c92b2b",
          port: "제주공항",
          content: "급변풍 (08.06 16 : 22~ 08.06 18:00 KST)",
        },
      ],
      drivingStats: {
        date: "2024.07.25",
        data: [
          {
            subject: "운행율",
            value: "95%",
          },
          {
            subject: "안전 운행 평균 지수",
            value: "98",
          },
          {
            subject: "차량단말기",
            value: "1000",
          },
          {
            subject: "조업자 앱 사용율",
            value: "95%",
          },
          {
            subject: "신규등록 요청",
            value: "5",
          },
        ],
      },
      drivingStatsIssues: [
        {
          type: "긴급",
          color: "#c62b2e",
          content:
            "공항기상 레이더 (TDWR) 정기(월간) 점검이 있습니다. 다음과 날짜와 시간을 필히 확인…",
          created_at: "24.07.24 06:10:33",
        },
        {
          type: "공지",
          color: "#82818d",
          content: "조업사 안전 업무강화 실시",
          created_at: "24.07.24 06:10:33",
        },
      ],
      driveLog: {
        title: "차량운행 현황",
        tableHeaders: [
          { headerName: "조업사", field: "company" },
          { headerName: "조업자", field: "name" },
          { headerName: "배차차량", field: "vehicle" },
          { headerName: "배차시간", field: "dispatchTime" },
          { headerName: "차량위치", field: "vehicleLocation" },
          { headerName: "연결상태", field: "connectionStatus" },
          { headerName: "차량속도", field: "speed" },
          { headerName: "알람", field: "alarm" },
          { headerName: "상태", field: "status" },
        ],
        data: [
          {
            company: "제주에어",
            name: "김조업",
            vehicle: "스켑카(01)",
            dispatchTime: "6:20",
            vehicleLocation: "37탑승교",
            connectionStatus: "양호",
            speed: "30km/h",
            alarm: "전송중",
            status: "조업중",
          },
          {
            company: "케이에이",
            name: "김조업",
            vehicle: "스켑카(01)",
            dispatchTime: "6:20",
            vehicleLocation: "37탑승교",
            connectionStatus: "양호",
            speed: "30km/h",
            alarm: "속도위반",
            status: "강제정지",
          },
          {
            company: "한국공항",
            name: "김조업",
            vehicle: "스켑카(01)",
            dispatchTime: "6:20",
            vehicleLocation: "37탑승교",
            connectionStatus: "양호",
            speed: "30km/h",
            alarm: "전송중",
            status: "조업중",
          },
          {
            company: "티웨이에어",
            name: "김조업",
            vehicle: "스켑카(01)",
            dispatchTime: "6:20",
            vehicleLocation: "37탑승교",
            connectionStatus: "양호",
            speed: "30km/h",
            alarm: "전송중",
            status: "조업중",
          },
          {
            company: "스위스포트",
            name: "김조업",
            vehicle: "스켑카(01)",
            dispatchTime: "6:20",
            vehicleLocation: "37탑승교",
            connectionStatus: "양호",
            speed: "30km/h",
            alarm: "전송중",
            status: "조업중",
          },
          {
            company: "고암에이스",
            name: "김조업",
            vehicle: "스켑카(01)",
            dispatchTime: "6:20",
            vehicleLocation: "37탑승교",
            connectionStatus: "양호",
            speed: "30km/h",
            alarm: "전송중",
            status: "조업중",
          },
          {
            company: "케이에이",
            name: "김조업",
            vehicle: "스켑카(01)",
            dispatchTime: "6:20",
            vehicleLocation: "37탑승교",
            connectionStatus: "양호",
            speed: "30km/h",
            alarm: "전송중",
            status: "조업중",
          },
          {
            company: "티웨이에어",
            name: "김조업",
            vehicle: "스켑카(01)",
            dispatchTime: "6:20",
            vehicleLocation: "37탑승교",
            connectionStatus: "양호",
            speed: "30km/h",
            alarm: "전송중",
            status: "조업중",
          },
          {
            company: "스위스포트",
            name: "김조업",
            vehicle: "스켑카(01)",
            dispatchTime: "6:20",
            vehicleLocation: "37탑승교",
            connectionStatus: "양호",
            speed: "30km/h",
            alarm: "전송중",
            status: "조업종료",
          },
          {
            company: "고암에이스",
            name: "김조업",
            vehicle: "스켑카(01)",
            dispatchTime: "6:20",
            vehicleLocation: "37탑승교",
            connectionStatus: "양호",
            speed: "30km/h",
            alarm: "전송중",
            status: "조업종료",
          },
        ],
      },
      driveLogSearchOptions: [
        { name: "전체", value: "_" },
        { name: "에어코리아", value: "에어코리아" },
        { name: "케이에이", value: "케이에이" },
        { name: "제주에어", value: "제주에어" },
        { name: "티웨이", value: "티웨이" },
        { name: "이스타포트", value: "이스타포트" },
        { name: "고암에이스", value: "고암에이스" },
        { name: "샤프", value: "샤프" },
      ],
      driveLogSearchValue: "_",
    }
  },
  methods: {
    formatNow(date) {
      return moment().locale("ko").format("YYYY.MM.DD(ddd) HH:mm:ss")
    },
    formatDate(date, format) {
      return moment(date).format(format)
    },
  },
}
</script>

<template>
  <div id="app">
    <header>
      <div class="now">
        <span>{{ formatNow(now) }}</span>
      </div>
      <div>
        <img src="./assets/images/logo-kac.png" alt="" class="logo" />
      </div>
      <div class="actions">
        <span class="page-title">GIMPO Airport AVCS V2 통합대시보드</span>
        <Button>
          <img src="./assets/icons/ic-set.svg" alt="" text />
        </Button>
        <Button>
          <img src="./assets/icons/ic-out.svg" alt="" text />
        </Button>
      </div>
    </header>
    <main>
      <div class="map-contanier">
        <div class="viewer">
          <nav>
            <div v-for="menu in viewerMenu" class="menu">
              <Button>{{ menu.title }}</Button>
            </div>
          </nav>
        </div>
        <div class="player"></div>
      </div>
      <div class="info-container">
        <section class="counts">
          <div
            v-for="info in countsData"
            class="info"
            :style="{ backgroundColor: info.color }"
          >
            <div>{{ info.title }}</div>
            <div>{{ info.count }}</div>
          </div>
        </section>

        <section class="environment">
          <div class="wrap">
            <div class="weather item content-item-box">
              <img src="./assets/images/ic-rain.png" alt="" />
              <div>기온 26.2</div>
              <div>습도 99.9</div>
            </div>
            <div v-for="item in environmentData" class="item content-item-box">
              <div class="caption">{{ item.caption }}</div>
              <div class="subject">{{ item.subject }}</div>
              <div class="value">{{ item.value }}</div>
            </div>
          </div>
          <div class="issue-wrap">
            <div class="issue-box">
              <div
                class="badge"
                :style="{ backgroundColor: environmentIssues[0].color }"
              >
                {{ environmentIssues[0].type }}
              </div>
              <div class="content">{{ environmentIssues[0].content }}</div>
            </div>

            <div class="divider"></div>

            <div class="issue-box">
              <div
                class="badge"
                :style="{ backgroundColor: environmentIssues[0].color }"
              >
                {{ environmentIssues[0].type }}
              </div>
              <div class="content">{{ environmentIssues[0].content }}</div>
            </div>
          </div>
        </section>

        <section class="drive-status">
          <div class="text-white date">
            {{ formatDate(drivingStats.date, "YYYY.MM.DD") }} 기준
          </div>
          <div class="wrap">
            <div
              v-for="item in drivingStats.data"
              class="item content-item-box"
            >
              <div class="caption">{{ item.caption }}</div>
              <div class="subject">{{ item.subject }}</div>
              <div class="value">{{ item.value }}</div>
            </div>
          </div>

          <div class="issue-wrap">
            <div v-for="issue in drivingStatsIssues" class="issue">
              <span class="type" :style="{ backgroundColor: issue.color }">{{
                issue.type
              }}</span>
              <div class="content">{{ issue.content }}</div>
              <span class="caption">{{ issue.created_at }}</span>
            </div>
          </div>
        </section>
        <section class="tables">
          <div class="btn-line flex">
            <Button label="차량운행 현황" />
            <Button label="Ads-B 정보" />
            <Button label="항공 스케줄" />
            <Button label="알림목록" />
            <Button>
              <img src="./assets/icons/ic-refresh-time.svg" alt="" />
            </Button>
          </div>

          <Tabs :value="driveLogSearchValue">
            <TabList>
              <Tab v-for="tab in driveLogSearchOptions" :value="tab.value">{{
                tab.name
              }}</Tab>
            </TabList>
            <TabPanels>
              <TabPanel v-for="tab in driveLogSearchOptions" :value="tab.value">
                <DataTable :value="driveLog.data">
                  <Column
                    v-for="col in driveLog.tableHeaders"
                    :header="col.headerName"
                    :field="col.field"
                  />
                </DataTable>
              </TabPanel>
            </TabPanels>
          </Tabs>
        </section>
      </div>
    </main>
  </div>
</template>

<style scoped lang="scss">
header {
  padding: 1.438rem 1.563rem 1.375rem 3rem;
  border-radius: 20px;
  border: solid 1px #594e24;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

main {
  display: flex;
  width: 100%;
}

.now {
  color: #ffffff;
  font-size: 2.125rem;
  font-weight: bold;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: 0.68px;
}

header {
  .actions {
    display: flex;
    align-items: center;

    .page-title {
      font-size: 1.875rem;
      font-weight: 500;
      font-stretch: normal;
      font-style: normal;
      line-height: normal;
      letter-spacing: normal;
      color: #c9aa2b;
      margin-right: 1.875rem;
    }

    button {
      background-color: transparent;
      border: none;
    }

    button + button {
      margin-left: 1.25rem;
    }
  }
}

main {
  .container {
    .viewer {
      position: relative;
      padding: 1.25rem 1.5rem 5.875rem;
      border-radius: 10px;
    }
  }
}

nav {
  // position: absolute;
  display: flex;
  align-items: center;
}

.menu {
  button {
    padding: 1.25rem;
    display: flex;
    justify-content: center;
    align-items: center;

    border-radius: 10px;
    background-image: linear-gradient(
      to bottom,
      rgba(0, 0, 0, 0.2),
      rgba(34, 34, 34, 0)
    );
    background-color: #222;
    font-size: 2rem;
    font-weight: 500;
    letter-spacing: -1.6px;
    text-align: center;

    color: #766626;
  }

  button + button {
    margin-left: 1.125rem;
  }
}

.info-container {
  section {
    padding: 1.875rem 1.5rem 1.875rem 1.563rem;
    border-radius: 10px;
    background-color: #333023;
  }

  section + section {
    margin-top: 1.25rem;
  }
}

.counts {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 1.25rem;

  .info {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    padding: 2.125rem 4.063rem 2.125rem 4.125rem;
    border-radius: 10px;

    font-size: 2.375rem;
    color: #fff;
    letter-spacing: -0.76px;
    font-weight: 500;
  }
}

.content-item-box {
  padding: 1.425rem 2.111rem 1.125rem 2.111rem;
  border-radius: 20px;
  background-color: #263761;
  color: #fff;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  font-size: 1.25rem;

  & + & {
    margin-left: 1.25rem;
  }

  .caption,
  .subject {
    color: #9bb8ff;
  }

  .caption {
    font-size: 1.188rem;
    font-weight: 500;
    letter-spacing: -0.57px;
  }

  .subject {
    font-size: 1.25rem;
    font-weight: 600;
  }

  .value {
    font-size: 2.375rem;
    font-weight: 500;
  }
}

.environment {
  .wrap {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    gap: 1.25rem;
  }

  .badge {
    margin-right: 0.75rem;
  }

  .issue-wrap {
    height: 5.5rem;

    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .divider {
    border-right: 1px solid #766626;
    width: 0px;
    height: 1.5rem;
  }

  .issue-box {
    display: flex;
    align-items: center;

    .badge {
      padding: 0.375rem 0.313rem 0.313rem;
      border-radius: 5px;
      margin-right: 0.625rem;
      font-size: 1.125rem;
      font-weight: 600;
      color: #fff;
    }

    .content {
      font-size: 1.25rem;
      letter-spacing: -0.72px;
      color: #fff;
    }
  }
}

.text-white {
  color: #fff;
}

.drive-status {
  .date {
    font-size: 1.25rem;
    font-weight: 300;
  }

  .wrap {
    display: flex;
  }

  .issue-wrap {
    margin-top: 2.5rem;
  }

  .issue {
    display: flex;
    align-items: center;
    color: #fff;

    & + & {
      margin-top: 1rem;
    }

    .type {
      border-radius: 5px;
      height: 2rem;
      font-size: 1.125rem;
      font-weight: 500;
      padding: 0.125rem 0.375rem 0.188rem;
      margin-right: 0.625rem;
    }

    .content {
      flex: 1;
      font-size: 1.5rem;
      margin-right: 0.875rem;
    }

    .caption {
      font-size: 1.125rem;
      font-weight: normal;
      color: #82818d;
    }
  }
}

.p-tab {
  font-size: 1.438rem;
  font-weight: bold;
  color: #fff;
}
.p-tab.p-tab-active {
  color: #c9aa2b;
  border-color: #c9aa2b;
}
.p-tablist-tab-list {
  background: transparent;
}
.p-tabpanels {
  background: transparent;
}
:deep(.p-datatable-header-cell) {
  background-color: #514823;
  color: #fff;
  font-size: 1.25rem;
  font-weight: 600;
  letter-spacing: -0.4px;
}
:deep(.p-datatable-tbody > tr) {
  background: transparent;
  color: #fff;

  font-size: 1.375rem;
  font-weight: 500;
  letter-spacing: -0.22px;
}
:deep(.p-datatable-tbody > tr > td),
:deep(.p-datatable-header-cell) {
  border-color: transparent;
}
</style>

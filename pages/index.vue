<template>
  <div>
    <div>
      <b-navbar toggleable="lg" type="light" variant="warning">
        <b-navbar-brand href="#">HỌC TRADE</b-navbar-brand>
      </b-navbar>
    </div>
    <div class="main">
      <b-row>
        <b-col md="3" lg="3" sm="12">
          <div class="accordion" role="tablist">
            <b-card no-body class="mb-2" v-for="(moduleVideo, index1) in listvideo" :key="index1">
              <b-card-header header-tag="header" class="p-1" role="tab">
                <b-button block v-b-toggle="moduleVideo.id" variant="info">{{ moduleVideo.moduleName }}
                </b-button>
              </b-card-header>
              <b-collapse :id="moduleVideo.id" role="tabpanel">
                <b-card-body>
                  <b-card-text class="listlink">
                    <ol>
                      <li class="mt-2" v-for="session, index2 in moduleVideo.sessionList" :key="index2">
                        <p v-b-toggle="moduleVideo.id + session.id" variant="primary">{{ session.nameSession }}
                          ({{ session.listVideoChild.length }})
                        </p>
                        <b-collapse :id="moduleVideo.id + session.id">
                          <ul>
                            <li v-for="video, index1 in session.listVideoChild" :key="index1">
                              <p class="card-text" @click="setVideo(video.src)">
                                {{ video.nameVideo }}
                              </p>
                            </li>
                          </ul>
                        </b-collapse>
                      </li>
                    </ol>

                  </b-card-text>
                </b-card-body>
              </b-collapse>
            </b-card>

          </div>
        </b-col>
        <b-col  md="9" lg="9" sm="12" class="mt-2">
          <div style="background-size: 100% 100%; background:url('bg.jpg')">
            <b-embed type="iframe" allow="autoplay" :src="urlMainVideo" allowfullscreen frameborder="0">
            </b-embed>
          </div>
        </b-col>
      </b-row>

    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      urlMainVideo: '',
      listvideo: [
        {
          id: 'module1',
          moduleName: "Module 1",
          sessionList: [
            {
              nameSession: "Một số vấn đề khi học",
              id: 0,
              listVideoChild: [{
                nameVideo: "Video giới thiệu",
                src: '3686693014147'
              }]
            },
            {
              nameSession: "Phân tích kĩ thuật và nghề trade",
              id: 1,
              listVideoChild: [
                {
                  nameVideo: "Định nghĩa cơ bản về giao dịch phái sinh crypto và nghề TRADE",
                  src: '3686693079683'
                }, {
                  nameVideo: "Trader cần làm gì để có lợi nhuận bền vững",
                  src: '3686693472899'
                }, {
                  nameVideo: "Các yếu tố cần quan tâm khi tham gia thị trường",
                  src: '3686693145219'
                },
              ]
            },
            {
              nameSession: "Quản lí vốn cơ bản và các yếu tố liên quan đến quản lí vốn",
              id: 2,
              listVideoChild: [
                {
                  nameVideo: "Tỉ lệ R:R Winrate quản lí vốn cơ bản",
                  src: '3686693210755'
                }, {
                  nameVideo: "Trò chơi tung đồng xu và bài học về quản lí vốn",
                  src: '3686693735043'
                }, {
                  nameVideo: "Tại sao các trader chuyên nghiệp luôn muốn bảo vệ vốn trước lợi nhuận sau ?",
                  src: '3686693603971'
                }, {
                  nameVideo: "Giải thích về đòn bẩy chi tiết",
                  src: '3686693341827'
                },
              ]
            }, {
              nameSession: "Các chỉ báo nên dùng trong giao dịch",
              id: 3,
              listVideoChild: [
                {
                  nameVideo: "Lý thuyết về các đường trung bình động MA,EMA",
                  src: '3686693276291'
                }, {
                  nameVideo: "Lý thuyết về Bollinger Band",
                  src: '3686693407363'
                }, {
                  nameVideo: "Thực hành chart kiểm chứng về Bollinger Band và MA",
                  src: '3686406621827'
                }, {
                  nameVideo: "Lý thuyết và hướng dẫn trên chart chỉ báo RSI",
                  src: '3686406752899'
                }, {
                  nameVideo: "Lý thuyết và thực hành với chỉ báo Stochasic",
                  src: '3686406687363'
                },
              ]
            }, {
              nameSession: "Cấu trúc thị trường, cấu trúc đường giá và xu hướng",
              id: 4,
              listVideoChild: [
                {
                  nameVideo: "Cấu trúc đường giá và điểm vào lệnh tốt nhất",
                  src: '3686407211651'
                }, {
                  nameVideo: "Xu hướng là gì và cách xác định xu hướng đơn giản nhất",
                  src: '3686406818435'
                }, {
                  nameVideo: "Bản đồ chiến tranh, vùng tranh chấp và xu hướng duy chuyển của giá",
                  src: '3686407146115'
                }, {
                  nameVideo: "Thống nhất về xác định xu hướng theo hệ thống giao dịch",
                  src: '3686407080579'
                }, {
                  nameVideo: "Khi nào xu hướng đảo chiều và nên làm gì khi xu hướng đảo chiều",
                  src: '3686406883971'
                }
              ]
            }, {
              nameSession: "Các yếu tố xác nhận mở lệnh",
              id: 5,
              listVideoChild: [
                {
                  nameVideo: "Câu chuyện của một cây nến và hỗ trợ kháng cự HK/KC",
                  src: '3686406949507'
                }, {
                  nameVideo: "Những mẫu nến dùng để xác nhận lệnh",
                  src: '3686407015043'
                }, {
                  nameVideo: "Tại sao nên chờ xác nhận 2 lần trước khi mở lệnh",
                  src: '3686616730243'
                }, {
                  nameVideo: "Mở lệnh khi có xác nhận nâng cao",
                  src: '3686616795779'
                },
              ]
            }, {
              nameSession: "Dừng lỗ và dừng lỗ hợp lí trong giao dịch",
              id: 6,
              listVideoChild: [
                {
                  nameVideo: "Stoploss bài 1",
                  src: '3686616861315'
                }, {
                  nameVideo: "Stoploss bài 2, ATR auto",
                  src: '3686616926851'
                }, {
                  nameVideo: "Stoploss bài 3, chờ đợi xác nhận của Market marker",
                  src: '3686616992387'
                }
              ]
            }, {
              nameSession: "Các vấn đề tâm lí trong giao dịch, rất quan trong",
              id: 7,
              listVideoChild: [
                {
                  nameVideo: "Sức chịu đựng 1% và mức target hợp lí trong giao dịch",
                  src: '3686617909891'
                }
              ]
            }, {
              nameSession: "Sử dụng PTTK khi hold và đầu tư SPOT",
              id: 8,
              listVideoChild: [
                {
                  nameVideo: "Sử dụng PTTK cho giao dịch SPOT và cơ hội HOLD",
                  src: '3686617057923'
                }, {
                  nameVideo: "Phòng hộ giao dịch SPOT bằng future để linh hoạt khi có lợi nhuận",
                  src: '3686617778819'
                }
              ]
            }, {
              nameSession: "Livestream thực tế",
              id: 9,
              listVideoChild: [
                {
                  nameVideo: "Livestream #1",
                  src: '3686617123459'
                }, {
                  nameVideo: "Livestream #2 Trading chắc chắn không dễ, có những lúc việc tốt nhất là không làm gì cả. Nhắc nhở ae bám sát phương pháp gd và theo sát lệnh khi chưa đưa được SL về entry",
                  src: '3686617844355'
                }, {
                  nameVideo: "Một số hướng dẫn khi giao dịch bằng binance và các lỗi không được vi phạm để CHÁY tài khoản",
                  src: '3686617188995'
                }, {
                  nameVideo: "Kết hợp chỉ báo để gia tăng tỷ lệ thắng",
                  src: '3686617647747'
                }, {
                  nameVideo: "Quan điểm về HT/KC mạnh yếu và thực hành lệnh trực tiếp",
                  src: '3686617254531'
                }
              ]
            }
          ]
        }
        , {
          id: 'module2',
          moduleName: "Module 2",
          sessionList: [
            {
              nameSession: "Một số chỉ báo nâng cao nên dùng",
              id: 0,
              listVideoChild: [{
                nameVideo: "Lý thuyết về chỉ báo Fibonacci Hồi Quy ( thoái lui)",
                src: '3686617713283'
              }, {
                nameVideo: "Sử dụng fibo thoái lui và thực hành",
                src: '3686617320067'
              }, {
                nameVideo: "Lý thuyết về chỉ báo MACD và ADX DMI + thực hành chart",
                src: '3686617385603'
              }, {
                nameVideo: "Cách áp dụng MACD vào chiến lược giao dịch",
                src: '3688328858243'
              }, {
                nameVideo: "Các áp dụng ADX vào hệ thống giao dịch",
                src: '3688328923779'
              }]
            },
            {
              nameSession: "Các tool bổ sung trong quá trình giao dịch",
              id: 1,
              listVideoChild: [
                {
                  nameVideo: "CryptoQuant : BTC exchange Netflow",
                  src: '3688328792707'
                }, {
                  nameVideo: "CryptoQuant : BTC Fundingrate",
                  src: '3688329972355'
                }
              ]
            },
            {
              nameSession: "Khung thời gian và phân tích đa khung thời gian",
              id: 2,
              listVideoChild: [
                {
                  nameVideo: "Lý thuyết về đa khung thời gian (Timeframe)",
                  src: '3688330037891'
                }, {
                  nameVideo: "Vận dụng phân tích đa khung thời gian và thực hành chart",
                  src: '3688330103427'
                }
              ]
            }, {
              nameSession: "Volume và cách đọc nến + volume để hiểu về xu hướng",
              id: 3,
              listVideoChild: [
                {
                  nameVideo: "Volume giao dịch và tick volume có dùng phân tích được không ?",
                  src: '3688330431107'
                }, {
                  nameVideo: "Tính chủ quan khi phân tích Volume giao dịch",
                  src: '3688330168963'
                }, {
                  nameVideo: "Dùng Volume để xác nhận một xu hướng và phân tích cây nến",
                  src: '3688330300035'
                }, {
                  nameVideo: "Phân tích xu hướng tiếp diễn thế nào bằng cách mổ xẻ xu hướng bằng volume",
                  src: '3688330234499'
                }, {
                  nameVideo: "Phân loại volume theo độ cao và ứng dụng để nhận ra xu hướng suy yếu",
                  src: '3688330562179'
                }, {
                  nameVideo: "Nến SC và nến BC, dấu hiệu bắt đầu một cú đảo chiều xu hướng",
                  src: '3688330365571'
                }, {
                  nameVideo: "Nến DT, tín hiệu mạnh để LONG ngược xu hướng",
                  src: '3688335739523'
                }, {
                  nameVideo: "Nến UT, tín hiệu mạnh để SHORT ngược xu hướng",
                  src: '3686617582211'
                }, {
                  nameVideo: "Nến E<R, Nổ lực ít mà kết quả cao, dấu hiệu của một cú phá vỡ giả",
                  src: '3688339671683'
                }, {
                  nameVideo: "Nến E>R, Nỗ lực nhiều mà ket61 quả không bao nhiêu, dấu hiệu mạnh để đảo chiều xu hướng",
                  src: '3688339606147'
                },
              ]
            }, {
              nameSession: "Một số kinh nghiệm và TIP trong giao dịch",
              id: 4,
              listVideoChild: [
                {
                  nameVideo: "Nhận ra thị trường sideway và cách giao dịch trong thị trường SW",
                  src: '3688339868291'
                }
              ]
            }, {
              nameSession: "Livestream",
              id: 5,
              listVideoChild: [
                {
                  nameVideo: "Livestream #1",
                  src: '3688339999363'
                }, {
                  nameVideo: "Livestream #2, chiến thuật scalping mày không chết tao chết. Trading không có đúng sai, còn tiền là còn đúng",
                  src: '3688339802755'
                }, {
                  nameVideo: "Livestream #3",
                  src: '3688339737219'
                }
              ]
            }, {
              nameSession: "Tổng hợp các lời khuyên và các vấn đề cần nhớ khi THỰC CHIẾN",
              id: 6,
              listVideoChild: [
                {
                  nameVideo: "Theo dõi xu hướng BTC khi trade altcoin để luôn ứng biến",
                  src: '3688339933827'
                }
              ]
            }
          ]
        }
        , {
          id: 'module3',
          moduleName: "Module 3",
          sessionList: [
            {
              nameSession: "Các ý tưởng dưới góc nhìn của cá mập khi nghĩ về thị trường",
              id: 0,
              listVideoChild: [{
                nameVideo: "Intro và chia sẽ quan điểm đầu tư vào thị trường crypto",
                src: '3688358611587'
              }, {
                nameVideo: "Sườn ý tưởng để tìm một cơ hội tiềm năng",
                src: '3686687705731'
              }, {
                nameVideo: "Nhận biết 1 trend và cơ hội khi trend được hình thành",
                src: '3686687640195'
              }, {
                nameVideo: "Price Cycle chu kì đường giá",
                src: '3686687574659'
              }, {
                nameVideo: "5 sóng Elliot Lớn và lựa chọn nhịp để tham gia",
                src: '3686688033411'
              }]
            },
            {
              nameSession: "Các tiêu chí để phân tích và đánh giá dự án có tiềm năng hay không",
              id: 1,
              listVideoChild: [
                {
                  nameVideo: "Đánh giá tiềm năng tăng trưởng khi theo dõi biến động ví HOLDER",
                  src: '3686687509123'
                }, {
                  nameVideo: "Market Cap hiểu đúng và tư duy theo Market Marker",
                  src: '3686687771267'
                }, {
                  nameVideo: "Token usecase, Tokenomics . Hiểu cách Token chạy để biết giá token đi về đâu",
                  src: '3686687902339'
                }, {
                  nameVideo: "TLV Biết dòng tiền đến hay đi sẽ biết giá tăng hay giảm",
                  src: '3686687836803'
                }, {
                  nameVideo: "Crypto Miso Cách kiếm dự án có đang tiếp tục phát triển và khả năng hoàn thành Roadmap - Chưa có",
                  src: '3686693603971'
                },
              ]
            },
            {
              nameSession: "Các công cụ để phân tích dự án và theo dấu cá mập",
              id: 2,
              listVideoChild: [
                {
                  nameVideo: "Các dịch thông tin tiếng anh sang tiếng việt",
                  src: '3686687967875'
                }, {
                  nameVideo: "Tìm kiếm dự án theo danh mục đầu tư bằng crunchbase và messari",
                  src: '3686673746563'
                }, {
                  nameVideo: "Kyper Discovery - Công cụ tìm kèo trade ngắn hạn mà hiệu quả cao",
                  src: '3686673615491'
                }, {
                  nameVideo: "Biết các cập nhật sắp tới với lịch sự kiên của Messari",
                  src: '3686673812099'
                }, {
                  nameVideo: "Lọc coin lowcap trên sàn CEX để tìm kiếm tiềm năng",
                  src: '3686673877635'
                }, {
                  nameVideo: "Cách nhận ra đỉnh đáy dưới góc nhìn tâm lý của Market Maker Missing",
                  src: '3686693603971'
                }, {
                  nameVideo: "Nansen - lần theo dòng tiền SMART MONEY để kiếm ăn cùng cá lớn",
                  src: '3686673943171'
                },
              ]
            }, {
              nameSession: "Thời điểm vàng để xuống tiền hoặc chốt lời theo dấu chân của cá mập",
              id: 3,
              listVideoChild: [
                {
                  nameVideo: "Dấu hiệu cú đẩy tiềm năng khi VOLUME tăng đột biến",
                  src: '3686674074243'
                }, {
                  nameVideo: "Đẩy thử đẩy thật - Quy trình thẩm định phản ứng thị trường của MM trước khi đẩy giá ",
                  src: '3686674008707'
                }, {
                  nameVideo: "Cách theo dấu quỹ để thoát hàng khi quỹ bán",
                  src: '3686674139779'
                }
              ]
            }, {
              nameSession: "Tổng kết và ví dụ cụ thể",
              id: 5,
              listVideoChild: [
                {
                  nameVideo: "Tổng hợp quy trình TÌM - LỌC - MUA - CHỐT lời theo dấu cá mập Missing",
                  src: '3686693603971'
                }
              ]
            }
          ]
        }
        ,


      ]
    }
  },
  methods: {
    setVideo(url) {
      this.urlMainVideo = `//ok.ru/videoembed/${url}?autoplay=1`
    }
  }

}
</script>
<style scoped>
.listlink p:hover {
  cursor: pointer;
  color: blue;
}
</style>
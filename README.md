# US Market Clock

美股及韩国股票市场交易时钟。美股按纽约时区自动切换夏令时与冬令时，内置 2026–2028 年休市日及半日市；韩国内置 2026 年休市日。超出日历覆盖范围或未核实的特殊交易日不显示精确交易倒计时。

## Calendar Scope

- 美股全天休市与半日市：[纽约证交所官方日历](https://www.nyse.com/trade/hours-calendars)、[纳斯达克 2026 年日历](https://www.nasdaqtrader.com/trader.aspx?id=Calendar)。半日市正股美东 13:00 收盘，盘后按纽约证交所电子市场 17:00 结束计算；券商可能有不同安排。
- 韩国：[交易所股票时段和休市规则](https://global.krx.co.kr/contents/GLB/06/0602/0602020204/GLB0602020204T1.jsp)、[2026 年官方月历说明](https://www.kasi.re.kr/publication/post/newsMaterial/32031)、[劳动节与制宪节新增公休日公告](https://www.mpm.go.kr/mpm/comm/newsPress/newsPressRelease/?boardId=bbs_0000000000000029&cntId=4250&mode=view&pageIdx=1)。年末另有交易所休市日。韩国仅覆盖 2026 年，后续年份需核实录入。
- 韩国盘前仅指 08:30–08:40 收盘价交易，不含大宗交易；08:40–09:00 不能算作持续交易。盘后包含 15:40–16:00 收盘价交易及后续延长时段，2026-09-14 起延长至 20:00。当前官方规则及[三星证券 9 月 14 日制度变更公告索引](https://www.samsungpop.com/customer/guide.do?MenuSeqNo=24418&cmd=notice_view&menuNo=020306)可交叉核对，不含其他交易所或特定品种保证。
- 2026-01-02 新年首个交易日、2026-11-19 韩国高考日有特殊安排，本次未核实完整交易所时段，显示待确认，不使用普通时段替代，也不当作全天休市。
- 核对日期：2026-11-02。不覆盖临时休市、停牌、熔断或夜盘；时间来自设备系统时钟。日历不是实时交易可用性数据源。

## Tests

```bash
node tests/market-time.test.cjs
```

修改 `index.html` 后同步 `us-market-clock.html`，两个入口应保持完全一致。

## Deploy to Vercel

1. 把本目录推送到 GitHub。
2. 在 Vercel 新建 Project，导入这个 GitHub 仓库。
3. Framework Preset 选择 `Other`。
4. Build Command 留空。
5. Output Directory 留空。
6. 部署完成后，在 Vercel 项目 `Settings -> Domains` 添加 `gupiao.94shengqian.com`。

## Local Preview

```bash
python -m http.server 4177
```

打开 `http://127.0.0.1:4177/`。

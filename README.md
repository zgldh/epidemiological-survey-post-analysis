# epidemiological-survey-post-analysis
# 传染病流行性调查结果分析

用于传染病流行性调查结果的转换、表示、分析和可视化。

## Schema 数据表示方法

``` TypeScript
interface SurveyResult {
{
    disesase: string,    // 传染病名称，如 "COVID-19",
    round: string,       // 疫情轮次，通常为`年-月`，或其他唯一标识
    cases: SurveyCase[], // 病例
};
```
``` TypeScript
interface SurveyCase {
    index: SurveyCaseIndex,     // 病例编号
    job?: string,               // 职业
    gender?: 'male'|'female',   // 性别
    addresses: SurveyCaseAddress[], // 地址 
    timeline: SurveyCaseTimelineItem[], // 病例行动时间线
    conclusion?: SurveyCaseConclusion, // 病例结论
}
```
``` TypeScript
interface SurveyCaseAddress{
    type: 'home'|'work'|'other', // 地址类型
    address: string,             // 地址
}
```
``` TypeScript
interface SurveyCaseTimelineItem{
    startAt: number, // 开始时间，Unix时间戳
    endAt: number,   // 结束时间，Unix时间戳
    location: string, // 地点
    action: string,   // 行为， 如购物、吃饭、出行等
}
```
``` TypeScript
interface SurveyCaseConclusion {
    type: 'diagnosed'|'symptomless'|'unknown', // 病例类型： diagnosed:确诊、symptomless:无症状、unknown:未知
    contacts: SurveyCaseContact[], // 有关联的病例列表
}
```
``` TypeScript
type SurveyCaseIndex = number;
```
``` TypeScript
interface SurveyCaseContact {
    index: SurveyCaseIndex, // 病例编号
    type: 'close'|'area'|'unknown', // 关联类型： close:密切接触、area:同区域、unknown:未知
}
```

## Transform 数据转换

1. TODO 将政府发布的自然语言流调报告，转换为本项目`Schema`格式的数据。

## Analysis 分析

1. TODO 自动填充 `SurveyCase.conclusion.contacts`
2. TODO 任选一个病例，找到其可能被哪个病例直接传染。
3. TODO 任选一个病例，找到其可能直接传染给了哪些病例。
4. TODO 任选两个病例，找到其之间传染联系。

## Visualization 可视化

1. TODO 生成病例传染图。
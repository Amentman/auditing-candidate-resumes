# Candidate Resume Auditing Skill

`auditing-candidate-resumes` 是一个面向 HR、招聘方和用人经理的 Codex Skill，用来审查候选人简历中的学历与专业、工作和项目时间线、Gap、岗位匹配、证据强度，以及经历夸大或真实性待核验信号。

它不会仅凭简历判断候选人“造假”或“能力差”，而是把材料明确陈述、有限推断、缺失信息和外部核验结果分开，并把关键疑点转成可执行的补材料或面试核验问题。

## 主要能力

- 重建教育、工作、项目、Gap 和重叠时间线。
- 区分硬门槛、岗位核心证据、加分项和未提及项。
- 拆分表达空泛、贡献归属不清和真实性矛盾。
- 给出推进、定向初筛、待补材料或不推进建议。
- 生成结论先行的正式报告：第一页先说明招聘动作、最多三个决定性问题和下一步。
- 对 Word、PDF 等正式报告提供颜色、表格、分页和逐页验收规范。

## 安装

```bash
git clone https://github.com/Amentman/auditing-candidate-resumes.git
ln -s "$(pwd)/auditing-candidate-resumes" ~/.codex/skills/auditing-candidate-resumes
```

安装后新开一个 Codex 会话，可以显式使用 `$auditing-candidate-resumes`，也可以让 Codex 根据候选人简历审查请求自动选择。

## 使用示例

```text
使用 $auditing-candidate-resumes，从 HR 和用人经理视角审查这份候选人简历，并结合岗位 JD 输出结论先行的 Word 报告。重点检查学历专业、工作和项目时间线、Gap、岗位匹配、贡献归属和真实性待核验点。
```

没有 JD 时，Skill 仍可做简历完整性、时间线和证据质量审查，但不会猜测具体岗位匹配标准。

## 仓库结构

```text
auditing-candidate-resumes/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── audit-framework.md
    ├── decision-first-report-design.md
    └── output-contract.md
```

## 核心边界

- 简历写明的内容属于候选人陈述，不等于已经外部验真。
- “没写”不等于“不会”；缺学校、日期或项目归属可以阻断流程，但不自动构成造假风险。
- Gap、短任期、专业不对口或普通学校不能直接转换为能力、稳定性或诚信结论。
- 只有获得授权并读取可靠外部证据后，才能把学历、任职、职位或业绩标为已核验。
- 不使用疾病、婚育、家庭责任、民族、宗教、残障、性别、年龄等敏感特征做筛选或排序。

## 验证

如果本机安装了 Codex 自带的 `skill-creator`，可运行：

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py .
```

正式 Word/PDF 报告还需要实际渲染并逐页检查；文件能打开不代表排版和阅读路径已经合格。

## 隐私

本仓库只包含通用审查框架和输出规范，不包含候选人简历、岗位内部资料、评估报告、生产凭据或个人绝对路径。

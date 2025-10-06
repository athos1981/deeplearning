# 规范驱动开发（SDD）

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#specification-driven-development-sdd)

## 能量反转

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#the-power-inversion)

几十年来，代码一直是王道。规范服务于代码——它们是我们搭建的脚手架，一旦“真正的”编码工作开始，它们就被丢弃。我们编写项目需求文档 (PRD) 来指导开发，创建设计文档来指导实现，绘制图表来可视化架构。但这些始终服从于代码本身。代码就是真理。其他一切，充其量也不过是美好的愿望。代码是真理的源泉，随着代码的推进，规范很少能跟上它的步伐。由于资产（代码）和实现合二为一，如果不尝试从代码构建，就很难实现并行实现。

规范驱动开发 (SDD) 颠覆了这种权力结构。规范不服务于代码，而是代码服务于规范。产品需求文档 (PRD) 并非实施指南，而是生成实施的源泉。技术计划并非指导编码的文档，而是生成代码的精确定义。这并非对我们软件构建方式的渐进式改进，而是对开发驱动力的根本性反思。

自软件开发诞生以来，规范与实现之间的差距一直困扰着它。我们尝试通过更完善的文档、更详细的需求和更严格的流程来弥合这一差距。这些方法最终失败了，因为它们认为差距不可避免。它们试图缩小差距，却从未消除它。软件驱动开发 (SDD) 通过使规范及其基于规范的具体实现计划可执行化来消除差距。当规范和实现计划生成代码时，差距就不存在了，只有转换。

这种转变如今之所以成为可能，是因为人工智能能够理解并执行复杂的规范，并制定详细的实施计划。然而，缺乏结构的原始人工智能生成会产生混乱。系统设计驱动（SDD）通过规范和后续的实施计划提供了这种结构，这些规范和实施计划足够精确、完整且明确，足以生成可运行的系统。规范成为主要的产物。代码则成为其在特定语言和框架中的表达（作为实施计划的实现）。

在这个新世界中，维护软件意味着不断发展规范。开发团队的意图通过自然语言（“**意图驱动开​​发**”）、设计资产、核心原则和其他指南来表达。开发的**通用语言**提升到了更高的层次，而代码则是最后一英里的途径。

调试意味着修复规范及其生成错误代码的实现计划。重构意味着为了清晰起见而进行重构。整个开发流程围绕规范进行重组，规范是核心事实来源，而实现计划和代码则是不断更新的输出。由于我们富有创造力，所以使用新功能更新应用程序或创建新的并行实现，意味着重新审视规范并创建新的实现计划。因此，这个过程就像一个 0 -> 1，(1', ..), 2, 3, N 的过程。

开发团队专注于他们的创造力、实验和批判性思维。

## SDD 工作流程实践

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#the-sdd-workflow-in-practice)

工作流程始于一个想法——通常模糊且不完整。通过与人工智能的迭代对话，这个想法最终会变成一份全面的项目需求文档 (PRD)。人工智能会提出澄清问题，识别边缘案例，并帮助定义精确的验收标准。传统开发中可能需要数天的会议和文档工作，现在只需数小时的专注规范工作即可完成。这改变了传统的软件开发生命周期 (SDLC)——需求和设计成为持续的活动，而非离散的阶段。这支持**团队流程**，在该流程中，团队评审的规范会被表达和版本化，在分支中创建并合并。

当产品经理更新验收标准时，实施计划会自动标记受影响的技术决策。当架构师发现更好的模式时，PRD 会进行更新以反映新的可能性。

在整个规范制定过程中，研究代理会收集关键背景信息。他们会调查库兼容性、性能基准和安全隐患。组织约束会被自动发现并应用——贵公司的数据库标准、身份验证要求和部署策略会无缝集成到每个规范中。

从项目需求文档 (PRD) 出发，AI 生成将需求映射到技术决策的实施计划。每项技术选择都有记录在案的依据。每个架构决策都追溯到具体需求。在整个过程中，一致性验证不断提升质量。AI 分析规范中的模糊性、矛盾性和差距——这不是一次性的门槛，而是一个持续的改进过程。

一旦规范及其实现计划足够稳定，代码生成就会开始，但它们不必“完整”。早期的生成可能只是探索性的——测试规范在实践中是否合理。领域概念变成了数据模型。用户故事变成了 API 端点。验收场景变成了测试。这通过规范将开发和测试融合在一起——测试场景不是在代码之后编写的，而是规范的一部分，用于生成实现和测试。

反馈循环的延伸超越了初始开发阶段。生产指标和事件不仅会触发修补程序，还会更新下一次更新的规范。性能瓶颈会成为新的非功能性需求。安全漏洞会成为影响所有后续版本的制约因素。规范、实施和运营现实之间的这种反复循环，是真正理解的诞生之地，也是传统软件开发生命周期 (SDLC) 转变为持续演进的契机。

## 为什么SDD现在如此重要

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#why-sdd-matters-now)

三种趋势使得 SDD 不仅成为可能，而且成为必要：

首先，人工智能的能力已经达到了一定的门槛，自然语言规范能够可靠地生成工作代码。这并不是要取代开发人员，而是要通过自动化从规范到实现的机械转换来提升他们的效率。它可以增强探索和创造力，支持轻松“重新开始”，并支持加法、减法和批判性思维。

其次，软件复杂性持续呈指数级增长。现代系统集成了数十种服务、框架和依赖项。通过手动流程使所有这些部分与初始意图保持一致变得越来越困难。软件驱动开发 (SDD) 通过规范驱动的生成提供系统性的一致性。框架可能会演变为提供 AI 优先的支持，而不是以人为本的支持，或者围绕可重用​​组件进行架构。

第三，变革步伐加快。如今，需求变化比以往任何时候都要快得多。调整不再是例外，而是意料之中的事。现代产品开发要求根据用户反馈、市场状况和竞争压力进行快速迭代。传统开发将这些变化视为干扰。每次调整都需要手动将变更传递到文档、设计和代码中。结果要么是缓慢而谨慎的更新，限制了速度；要么是快速而鲁莽的变更，积累了技术债务。

SDD 可以支持假设/模拟实验：“如果我们需要重新实施或更改应用程序以促进业务需求销售更多的 T 恤，我们将如何实施和实验？”

SDD 将需求变更从障碍转化为正常的工作流程。当规范驱动实施时，枢纽将成为系统性的再生，而非手动重写。更改 PRD 中的核心需求，受影响的实施计划将自动更新。修改用户故事，相应的 API 端点将重新生成。这不仅仅关乎初始开发，更关乎在不可避免的变更中保持工程速度。

## 核心原则

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#core-principles)

**规范作为通用语言**：规范成为主要的产物。代码成为其在特定语言和框架中的表达。维护软件意味着规范的不断演进。

**可执行规范**：规范必须足够精确、完整且明确，才能生成可运行的系统。这消除了意图与实现之间的差距。

**持续改进**：一致性验证是持续进行的，而非一次性的。AI 会持续分析规范中的模糊性、矛盾性和差距。

**研究驱动的背景**：研究代理在整个规范过程中收集关键背景，调查技术选项、性能影响和组织限制。

**双向反馈**：生产现实为规范的演进提供信息。指标、事件和运营经验都成为规范完善的输入。

**分支探索**：从同一规范生成多种实现方法，以探索不同的优化目标——性能、可维护性、用户体验、成本。

## 实施方法

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#implementation-approaches)

如今，实践 SDD 需要整合现有工具，并在整个过程中保持纪律。该方法可以通过以下方式进行实践：

- 用于迭代规范开发的人工智能助手
- 用于收集技术背景的研究代理
- 用于将规范转化为实现的代码生成工具
- 适用于规范优先工作流程的版本控制系统
- 通过人工智能分析规范文档进行一致性检查

关键是将规范视为真相的来源，将代码作为服务于规范的生成输出，而不是相反。

## 使用命令简化 SDD

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#streamlining-sdd-with-commands)

通过三个强大的命令自动执行规范→规划→任务工作流程，SDD 方法得到了显著增强：

### 命令`/specify`​

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#the-specify-command)

此命令将简单的功能描述（用户提示）转换为具有自动存储库管理的完整的结构化规范：

1. **自动特征编号**：扫描现有规格以确定下一个特征编号（例如，001、002、003）
2. **分支创建**：根据您的描述生成语义分支名称并自动创建
3. **基于模板的生成**：根据您的要求复制并定制功能规范模板
4. **目录结构**`specs/[branch-name]/`：为所有相关文档创建适当的结构

### 命令`/plan`​

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#the-plan-command)

一旦存在功能规范，此命令就会创建一个全面的实施计划：

1. **规范分析**：阅读并理解功能需求、用户故事和验收标准
2. **宪法合规性**：确保与项目章程和架构原则保持一致
3. **技术翻译**：将业务需求转化为技术架构和实施细节
4. **详细文档**：生成数据模型、API 合同和测试场景的支持文档
5. **快速启动验证**：生成快速启动指南，捕获关键验证场景

### 命令`/tasks`​

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#the-tasks-command)

创建计划后，该命令将分析该计划和相关设计文档以生成可执行任务列表：

1. **输入**：读取`plan.md`（必需）并且，如果存在`data-model.md`，，，`contracts/`和`research.md`
2. **任务派生**：将合约、实体、场景转化为具体的任务
3. **并行化**：标记独立任务`[P]`并概述安全并行组
4. **输出**：写入`tasks.md`功能目录，准备由任务代理执行

### 示例：构建聊天功能

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#example-building-a-chat-feature)

这些命令如何改变传统的开发工作流程：

**传统方法：**

```
1. Write a PRD in a document (2-3 hours)
2. Create design documents (2-3 hours)
3. Set up project structure manually (30 minutes)
4. Write technical specifications (3-4 hours)
5. Create test plans (2 hours)
Total: ~12 hours of documentation work
```

**使用命令方法的 SDD：**

```shell
# Step 1: Create the feature specification (5 minutes)
/specify Real-time chat system with message history and user presence

# This automatically:
# - Creates branch "003-chat-system"
# - Generates specs/003-chat-system/spec.md
# - Populates it with structured requirements

# Step 2: Generate implementation plan (5 minutes)
/plan WebSocket for real-time messaging, PostgreSQL for history, Redis for presence

# Step 3: Generate executable tasks (5 minutes)
/tasks

# This automatically creates:
# - specs/003-chat-system/plan.md
# - specs/003-chat-system/research.md (WebSocket library comparisons)
# - specs/003-chat-system/data-model.md (Message and User schemas)
# - specs/003-chat-system/contracts/ (WebSocket events, REST endpoints)
# - specs/003-chat-system/quickstart.md (Key validation scenarios)
# - specs/003-chat-system/tasks.md (Task list derived from the plan)
```

15 分钟后，您将获得：

- 包含用户故事和验收标准的完整功能规范
- 包含技术选择和基本原理的详细实施计划
- 已准备好生成代码的 API 契约和数据模型
- 自动化和手动测试的综合测试场景
- 所有文档均在功能分支中正确版本化

### 结构化自动化的力量

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#the-power-of-structured-automation)

这些命令不仅节省时间，还强制一致性和完整性：

1. **不会忘记细节**：模板确保考虑到每个方面，从非功能性需求到错误处理
2. **可追溯的决策**：每个技术选择都与特定需求相关
3. **动态文档**：规范与代码保持同步，因为它们生成代码
4. **快速迭代**：在几分钟内（而不是几天）更改需求并重新生成计划

这些命令将规范视为可执行的产物而非静态文档，从而体现了 SDD 原则。它们将规范流程从必要之恶转变为开发的驱动力。

### 模板驱动的质量：结构如何约束法学硕士以获得更好的结果

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#template-driven-quality-how-structure-constrains-llms-for-better-outcomes)

这些命令的真正威力不仅在于自动化，还在于模板如何引导LLM行为达到更高质量的规范。这些模板充当着复杂的提示，以高效的方式约束LLM的输出：

#### 1.**防止过早实施细节**

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#1-preventing-premature-implementation-details)

功能规范模板明确指示：

```
- ✅ Focus on WHAT users need and WHY
- ❌ Avoid HOW to implement (no tech stack, APIs, code structure)
```

这种约束迫使 LLM 保持适当的抽象级别。当 LLM 可能自然而然地跳到“使用 React 和 Redux 实现”时，该模板会使其专注于“用户需要实时更新数据”。这种分离确保了即使实现技术发生变化，规范也能保持稳定。

#### 2.**强制使用明确的不确定性标记**

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#2-forcing-explicit-uncertainty-markers)

两个模板都要求使用`[NEEDS CLARIFICATION]`标记：

```
When creating this spec from a user prompt:
1. **Mark all ambiguities**: Use [NEEDS CLARIFICATION: specific question]
2. **Don't guess**: If the prompt doesn't specify something, mark it
```

这可以防止 LLM 常见的行为，即做出看似合理但可能不正确的假设。LLM 不应猜测“登录系统”使用电子邮件/密码验证，而应将其标记为`[NEEDS CLARIFICATION: auth method not specified - email/password, SSO, OAuth?]`。

#### 3.**通过清单进行结构化思考**

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#3-structured-thinking-through-checklists)

模板包括作为规范“单元测试”的综合清单：

```md
### Requirement Completeness
- [ ] No [NEEDS CLARIFICATION] markers remain
- [ ] Requirements are testable and unambiguous
- [ ] Success criteria are measurable
```

这些清单迫使法学硕士（LLM）学生系统地自我审查其成果，以发现可能被忽略的不足之处。这就像为法学硕士（LLM）提供了一个质量保证框架。

#### 4.**通过大门遵守宪法**

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#4-constitutional-compliance-through-gates)

实施计划模板通过阶段门强制执行架构原则：

```md
### Phase -1: Pre-Implementation Gates
#### Simplicity Gate (Article VII)
- [ ] Using ≤3 projects?
- [ ] No future-proofing?
#### Anti-Abstraction Gate (Article VIII)
- [ ] Using framework directly?
- [ ] Single model representation?
```

这些门控通过让法学硕士（LLM）明确说明任何复杂性，从而防止过度设计。如果某个门控失败，法学硕士必须在“复杂性跟踪”部分记录原因，从而为架构决策建立问责机制。

#### 5.**分层细节管理**

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#5-hierarchical-detail-management)

模板强制执行适当的信息架构：

```
**IMPORTANT**: This implementation plan should remain high-level and readable.
Any code samples, detailed algorithms, or extensive technical specifications
must be placed in the appropriate `implementation-details/` file
```

这可以避免常见的规范变成难以阅读的代码转储的问题。LLM 学习保持适当的细节级别，将复杂性提取到单独的文件中，同时保持主文档的可导航性。

#### 6.**测试优先的思维**

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#6-test-first-thinking)

实施模板强制执行测试优先开发：

```
### File Creation Order
1. Create `contracts/` with API specifications
2. Create test files in order: contract → integration → e2e → unit
3. Create source files to make tests pass
```

这种排序约束确保 LLM 在实施之前考虑可测试性和合同，从而产生更强大和可验证的规范。

#### 7.**防止推测性特征**

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#7-preventing-speculative-features)

模板明确禁止猜测：

```
- [ ] No speculative or "might need" features
- [ ] All phases have clear prerequisites and deliverables
```

这样可以避免 LLM 添加一些“锦上添花”的功能，而这些功能会使实现变得复杂。每个功能都必须追溯到具体的用户故事，并有明确的验收标准。

### 复合效应

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#the-compound-effect)

这些约束共同作用，产生了以下规范：

- **完整**：检查清单确保不会遗漏任何内容
- **明确**：强制澄清标记突出不确定性
- **可测试**：测试优先的思维融入到流程中
- **可维护**：适当的抽象级别和信息层次
- **可实施**：明确的阶段和具体的可交付成果

这些模板将 LLM 从创意作家转变为训练有素的规范工程师，将其能力引导至始终如一地生成高质量、可执行的规范，真正推动发展。

## 宪法基础：加强建筑纪律

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#the-constitutional-foundation-enforcing-architectural-discipline)

SDD 的核心是章程——一套不可改变的原则，用于规范如何转化为代码。章程（`memory/constitution.md`）充当系统的架构 DNA，确保生成的每个实现都保持一致性、简洁性和高质量。

### 发展九条

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#the-nine-articles-of-development)

该宪法定义了九个条款，规范了发展过程的各个方面：

#### 第一条：图书馆优先原则

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#article-i-library-first-principle)

每个功能都必须以独立库的形式开始，没有例外。这迫使我们从一开始就采用模块化设计：

```
Every feature in Specify MUST begin its existence as a standalone library.
No feature shall be implemented directly within application code without
first being abstracted into a reusable library component.
```

这一原则确保规范生成模块化、可重用的代码，而不是单一的应用程序。当LLM生成实施计划时，它必须将功能构建为具有清晰边界和最小依赖关系的库。

#### 第二条：CLI 界面授权

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#article-ii-cli-interface-mandate)

每个库都必须通过命令行界面公开其功能：

```
All CLI interfaces MUST:
- Accept text as input (via stdin, arguments, or files)
- Produce text as output (via stdout)
- Support JSON format for structured data exchange
```

这增强了可观察性和可测试性。LLM 不能将功能隐藏在不透明的类中——所有内容都必须可以通过基于文本的接口访问和验证。

#### 第三条：测试优先原则

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#article-iii-test-first-imperative)

最具变革性的文章——测试前无代码：

```
This is NON-NEGOTIABLE: All implementation MUST follow strict Test-Driven Development.
No implementation code shall be written before:
1. Unit tests are written
2. Tests are validated and approved by the user
3. Tests are confirmed to FAIL (Red phase)
```

这完全颠覆了传统的AI代码生成方式。LLM不再是生成代码并寄希望于其能够正常工作，而是必须先生成定义行为的全面测试，获得批准后才能生成实现。

#### 第七和第八条：简单性和反抽象性

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#articles-vii--viii-simplicity-and-anti-abstraction)

以下文章旨在解决过度设计问题：

```
Section 7.3: Minimal Project Structure
- Maximum 3 projects for initial implementation
- Additional projects require documented justification

Section 8.1: Framework Trust
- Use framework features directly rather than wrapping them
```

当法学硕士（LLM）可能自然而然地创造出复杂的抽象概念时，这些文章会迫使其证明每一层复杂性的合理性。实施计划模板中的“第一阶段门”直接强化了这些原则。

#### 第九条：集成优先测试

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#article-ix-integration-first-testing)

优先进行真实世界测试而不是孤立的单元测试：

```
Tests MUST use realistic environments:
- Prefer real databases over mocks
- Use actual service instances over stubs
- Contract tests mandatory before implementation
```

这确保生成的代码在实践中有效，而不仅仅是在理论上。

### 通过模板执行宪法

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#constitutional-enforcement-through-templates)

实施计划模板通过具体的检查点将这些条款付诸实施：

```md
### Phase -1: Pre-Implementation Gates
#### Simplicity Gate (Article VII)
- [ ] Using ≤3 projects?
- [ ] No future-proofing?

#### Anti-Abstraction Gate (Article VIII)
- [ ] Using framework directly?
- [ ] Single model representation?

#### Integration-First Gate (Article IX)
- [ ] Contracts defined?
- [ ] Contract tests written?
```

这些门控在编译时对架构原则进行检查。如果未能通过这些门控，或在“复杂性跟踪”部分记录合理的异常，LLM 课程将无法继续进行。

### 不变原则的力量

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#the-power-of-immutable-principles)

宪法的力量在于其不可更改性。虽然实施细节可能会发生变化，但其核心原则始终保持不变。宪法规定：

1. **跨时间一致性**：今天生成的代码遵循与明年生成的代码相同的原则
2. **跨 LLM 的一致性**：不同的 AI 模型生成架构兼容的代码
3. **架构完整性**：每个功能都会强化而不是破坏系统设计
4. **质量保证**：测试优先、库优先和简单性原则确保代码可维护

### 宪法演变

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#constitutional-evolution)

虽然原则是不可改变的，但它们的应用可以演变：

```
Section 4.2: Amendment Process
Modifications to this constitution require:
- Explicit documentation of the rationale for change
- Review and approval by project maintainers
- Backwards compatibility assessment
```

这使得方法论在保持稳定性的同时能够不断学习和改进。宪法通过历次修订展现了自身的演变，展现了如何根据现实世界的经验不断完善原则。

### 超越规则：发展哲学

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#beyond-rules-a-development-philosophy)

章程不仅仅是一本规则手册，它是一种塑造 LLM 如何思考代码生成的哲学：

- **可观察性优于不透明性**：一切都必须可以通过 CLI 界面进行检查
- **简单胜过聪明**：从简单开始，只有在必要时才增加复杂性
- **集成优于隔离**：在真实环境中进行测试，而不是在人工环境中
- **模块化优于整体**：每个功能都是一个具有明确边界的库

通过将这些原则嵌入到规范和规划流程中，SDD 确保生成的代码不仅功能齐全，而且可维护、可测试且架构合理。该章程将 AI 从代码生成器转变为尊重并强化系统设计原则的架构合作伙伴。

## 转型

[](https://github.com/github/spec-kit/blob/main/spec-driven.md#the-transformation)

这并不是要取代开发人员或自动化创造力。而是要通过自动化机械翻译来增强人类的能力。这是为了创建一个紧密的反馈循环，让规范、研究和代码共同发展，每次迭代都能带来更深入的理解，并在意图和实现之间实现更好的协调。

软件开发需要更好的工具来维护意图与实现之间的一致性。软件驱动开发 (SDD) 提供了一种方法，通过可执行规范来生成代码，而不仅仅是指导代码，从而实现这种一致性。
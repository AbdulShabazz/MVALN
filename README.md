# MVALN

## Multi-Virtual-Machine Artificial Learning Network

The name reflects the architecture more accurately than MVALN because each learned opcode expression can be interpreted as a virtual machine performing a specialized transformation, while the full model coordinates multiple such machines.

The core definition becomes:

MVALN=learned virtual-machine program+learned opcode selection+learned operand bindings+persistent state+optional learned parameters

**Status:** Experimental research architecture  
**Model class:** Recursive opcode-based artificial learning system  
**Objective:** Replaces fixed artificial neural-network topology instead with a learned or synthesized executable program  

---

## Abstract

The Multi-Virtual-Machine Artificial Learning Network (MVALN) is a proposed alternative to conventional Artificial Neural Networks (ANNs).

A conventional ANN typically consists of:

```text
ANN =
    fixed computation graph
    + learned numerical parameters
```

MVALN instead represents a learned model as:

```text
MVALN =
    learned or synthesized opcode program
    + learned operand bindings
    + persistent state
    + optional learned numerical parameters
```

The primary learned object is not necessarily a matrix of connection weights. It may include:

* opcode selection,
* operand selection,
* expression topology,
* shared subexpressions,
* recurrent state transitions,
* constants,
* tensor parameters,
* instruction attributes,
* and program length.

Conventional ANN architectures are intended to remain expressible as a subset of MVALN.

---

## Motivation

Conventional ANNs generally begin with an engineer-defined architecture:

```text
Y = F(X, Θ)
```

Where:

* `F` is the fixed network topology,
* `X` is the input,
* `Θ` is the learned parameter set,
* `Y` is the output.

Training primarily modifies `Θ`. The structure of `F` normally remains fixed.

MVALN permits the computation itself to be learned:

```text
Y = Execute(Π, Θ, S₀, X)
```

Where:

* `Π` is an opcode program,
* `Θ` contains optional learned numerical parameters,
* `S₀` is the initial persistent state,
* `X` is the input.

The optimization objective may be expressed as:

```text
(Π*, Θ*) =
    argmin over Π and Θ of:

    TaskLoss(Execute(Π, Θ, S₀, X), Target)
    + λ × ProgramComplexity(Π)
```

MVALN therefore attempts to learn both:

```text
what values should be learned
```

and:

```text
what computation should be performed
```

---

## Core model

An MVALN expression is recursively defined as:

```text
Expression :=
      AtomicValue
    | Opcode(
          A: Expression?,
          B: Expression?,
          C: Expression?,
          D: Expression?,
          E: Expression?,
          Attributes?
      )
```

Each operand field is optional.

The fields are:

```text
A, B, C, D, E
```

An omitted operand is represented by the absence of that field. It is not replaced by numerical zero.

Example:

```text
ADD(
    A: Input.X,
    B: Input.X
)
```

Equivalent equation:

```text
X + X
```

The fields `C`, `D`, and `E` are absent.

---

## DNA/RNA-Inspired Constituent Design

MVALN is inspired not only by neuronal signaling, but by the biological instruction system that constructs, specializes, operates, and repairs organic neural networks.

A biological neural network does not begin as a fixed graph of neurons with assigned connection weights. Its constituent structure emerges through a layered process:

```text
DNA
→ transcription
→ RNA
→ translation and regulation
→ proteins and cellular machinery
→ differentiated neurons
→ synaptic organization
→ adaptive neural behavior
```

MVALN abstracts this process without attempting to simulate literal biochemistry.

The central design analogy is:

```text
DNA-like grammar
→ RNA-like instruction instances
→ virtual-machine execution
→ constituent specialization
→ network formation
→ adaptive behavior
```

### DNA-like persistent grammar

DNA provides a durable generative specification rather than directly executing every cellular operation.

The corresponding MVALN structure is a persistent grammar:

```text
Genome G =
    opcode vocabulary
    + operand-field rules
    + composition rules
    + type constraints
    + state-transition rules
    + program-generation rules
```

`G` defines the operations that may exist and the rules under which they may be composed.

It does not require every final program to be encoded explicitly.

Instead:

```text
Program Π =
    Develop(G, Context, State, Objective)
```

The resulting program may vary according to context while remaining derived from the same underlying grammar.

### RNA-like executable instructions

RNA is treated as the conceptual analogue of a transient, context-specific instruction instance.

An RNA-like MVALN instruction may be expressed as:

```text
Instruction mᵢ =
    Instantiate(
        Genome: G,
        Context: Cᵢ,
        State: Sᵢ,
        Inputs: Xᵢ
    )
```

The instruction contains:

```text
mᵢ =
    opcode
    + supplied operand fields
    + omitted operand fields
    + attributes
    + destination or effect
    + lifetime
```

For example:

```text
m₀ = ADD(
    A: X,
    B: X
)
```

or:

```text
m₁ = CONTRACT(
    A: Input,
    B: Parameter.W,
    indices: "bi,io->bo"
)
```

An instruction may be:

* created when required,
* executed locally,
* reused,
* modified,
* suppressed,
* duplicated,
* or discarded.

This differs from a conventional ANN layer, which normally remains permanently embedded in a fixed computation graph.

### Virtual machines as cellular constituents

Each MVALN virtual machine is analogous to an independently operating biological constituent.

A virtual machine contains:

```text
VMᵢ =
    local opcode program Πᵢ
    + local state Sᵢ
    + parameter set Θᵢ
    + input interface Iᵢ
    + output interface Oᵢ
```

Its state transition is:

```text
(Sᵢ[t + 1], Yᵢ[t]) =
    Execute(
        Program: Πᵢ,
        State: Sᵢ[t],
        Parameters: Θᵢ,
        Inputs: Xᵢ[t]
    )
```

Different virtual machines may develop different functional roles even when derived from the same grammar.

Examples include:

* feature extraction,
* routing,
* memory,
* comparison,
* prediction,
* error detection,
* state regulation,
* temporal integration,
* symbolic transformation,
* or program generation.

Specialization therefore occurs at the program level:

```text
VM role =
    SpecializedProgram(
        shared grammar,
        local context,
        execution history,
        task pressure
    )
```

### Constituent network formation

The complete MVALN is a network of interacting virtual machines:

```text
MVALN =
    {VM₀, VM₁, ..., VMₙ}
    + communication structure
    + shared environment
    + developmental rules
```

A virtual machine may consume outputs produced by other virtual machines:

```text
Xᵢ[t] =
    Route(
        Y₀[t],
        Y₁[t],
        ...,
        Yₙ[t],
        Context[t]
    )
```

The global system transition is:

```text
NetworkState[t + 1] =
    Compose(
        VM₀[t + 1],
        VM₁[t + 1],
        ...,
        VMₙ[t + 1]
    )
```

The network topology need not be permanently fixed.

Virtual machines and connections may be:

* created,
* removed,
* specialized,
* duplicated,
* merged,
* disabled,
* or reassigned.

### Development rather than fixed construction

A conventional ANN is usually constructed before training:

```text
Define topology
→ initialize parameters
→ optimize parameters
```

MVALN may instead develop its executable structure:

```text
Define grammar
→ instantiate programs
→ evaluate behavior
→ specialize constituents
→ alter communication
→ preserve effective structures
```

The model-development process may be written as:

```text
M[t + 1] =
    Develop(
        Model: M[t],
        Experience: E[t],
        Objective: J,
        Constraints: K
    )
```

Where `Develop` may alter:

```text
opcode selection
operand binding
program topology
virtual-machine count
virtual-machine specialization
state structure
communication topology
numerical parameters
```

### Regulation and conditional expression

Biological systems do not express every available instruction continuously. Activity depends on local conditions and regulatory signals.

MVALN applies the same principle:

```text
Enabled(mᵢ, t) =
    Predicate(
        Context[t],
        State[t],
        Inputs[t],
        RegulatorySignals[t]
    )
```

Execution becomes:

```text
Resultᵢ[t] =
    Execute(mᵢ)     when Enabled(mᵢ, t) is true
    NoOperation     otherwise
```

This permits context-dependent program expression without deleting the underlying capability.

A program may therefore exist in one of several states:

```text
inactive
primed
active
suppressed
retired
```

### Learning at multiple organizational levels

MVALN learning may occur simultaneously at several levels.

```text
Parameter learning =
    modify numerical values
```

```text
Instruction learning =
    modify opcodes, operands, or attributes
```

```text
Program learning =
    modify instruction composition
```

```text
Constituent learning =
    modify a virtual machine's specialization
```

```text
Network learning =
    modify virtual-machine communication and topology
```

```text
Developmental learning =
    modify the rules that generate future programs
```

The complete learning process may therefore be expressed as:

```text
Learning =
    parameter adaptation
    + opcode adaptation
    + operand adaptation
    + program adaptation
    + state adaptation
    + constituent specialization
    + network reorganization
    + grammar adaptation
```

### Biological correspondence

The intended abstraction is:

```text
Biological DNA
≈ persistent opcode grammar and developmental rules
```

```text
Biological RNA
≈ instantiated, transient, context-dependent instructions
```

```text
Proteins and molecular machinery
≈ primitive opcode implementations
```

```text
Cell
≈ stateful virtual machine
```

```text
Gene regulation
≈ conditional instruction activation
```

```text
Cell differentiation
≈ virtual-machine specialization
```

```text
Neural development
≈ program and communication-topology construction
```

```text
Synaptic plasticity
≈ runtime operand, parameter, routing, and state adaptation
```

```text
Organic neural network
≈ interacting population of specialized stateful machines
```

This correspondence is architectural rather than biochemical.

MVALN does not claim that software opcodes are chemically equivalent to RNA or that virtual machines reproduce living cells. The biological system provides a design principle:

```text
Complex adaptive intelligence may emerge from
a shared generative grammar,
context-specific instruction expression,
specialized stateful constituents,
and reorganizable communication.
```

### Constituent-design hypothesis

The MVALN constituent-design hypothesis is:

```text
A learning system may be more general when it learns
how to generate, specialize, regulate, and connect
executable constituents,
rather than only adjusting weights within
a predetermined network.
```

Accordingly:

```text
Conventional ANN =
    fixed constituent type
    + fixed topology class
    + learned connection parameters
```

Whereas:

```text
MVALN =
    generative instruction grammar
    + RNA-like executable programs
    + specialized virtual-machine constituents
    + adaptive communication topology
    + persistent and transient state
```

The model is therefore intended to emulate the organizational principle by which biological instruction systems construct neural machinery, rather than merely emulating the electrical output behavior of individual neurons.

## Operand-field semantics

The operand fields `A` through `E` are not physical processor registers.

They are symbolic operand fields within an instruction-expression grammar.

There is no restriction on:

* how often a field value may recur,
* where a value may occur,
* expression depth,
* expression width,
* shared references,
* recursive structure,
* recurrent state,
* or total program length.

The VLIW analogy describes the multi-operand capability of an instruction. It does not impose a physical register architecture.

Valid forms include:

```text
A + A
```

```text
A × B × A × C × A
```

```text
C(A + B(A + C))
```

```text
A[t + 1] = F(A[t], B[t], C[t])
```

```text
A[t + 1] = F(A[t], A[t - 1], B[t])
```

---

## Atomic values

An atomic expression may reference:

```text
Input[i]
Parameter[i]
State[i]
Constant[i]
```

These categories have distinct semantics.

### Input

External data supplied to the program:

```text
Input.Image
Input.TokenSequence
Input.SensorData
```

### Parameter

A learned numerical value or tensor:

```text
Parameter.W₀
Parameter.B₀
```

### State

A persistent value carried between execution steps:

```text
State.Hidden
State.Memory
State.Counter
```

### Constant

A fixed value:

```text
Constant.Zero
Constant.One
Constant.Epsilon
Constant.Pi
```

---

## Operand omission

Omission must not be confused with zero.

For example:

```text
ADD(A: X)
```

may be invalid if `ADD` requires at least two operands.

By contrast:

```text
ADD(
    A: X,
    B: Constant.Zero
)
```

is valid and computes:

```text
X + 0
```

The following are different:

```text
Field omitted
```

```text
Field contains zero
```

Zero is operation-dependent:

```text
X + 0 = X
X × 0 = 0
exp(0) = 1
max(X, 0) ≠ X in general
```

Each opcode must define:

* minimum arity,
* maximum arity,
* permitted fields,
* required fields,
* operand types,
* shape constraints,
* and omission behavior.

---

## Canonical motivating expression

The original motivating expression is:

```text
Root =
    C(
        E × exp(A(ABC + ABC))
        /
        D × exp(B(ABC + ABC))
    )
```

To avoid ambiguity between operand values and transformations, it may be written as:

```text
Root =
    OpC(
        E × exp(OpA(A × B × C + A × B × C))
        /
        D × exp(OpB(A × B × C + A × B × C))
    )
```

A shared-subexpression form is:

```text
T = A × B × C + A × B × C

N = E × exp(OpA(T))

D₀ = D × exp(OpB(T))

Root = OpC(N / D₀)
```

The shared form evaluates `T` once and reuses it.

---

## Tree, graph, and recurrent semantics

### Tree semantics

Repeated syntax denotes repeated evaluation:

```text
Y = F(G(X), G(X))
```

`G(X)` may be evaluated twice.

### Graph semantics

A named intermediate denotes shared evaluation:

```text
T = G(X)

Y = F(T, T)
```

`T` is evaluated once and reused.

Graph semantics permit:

* common-subexpression elimination,
* caching,
* skip connections,
* dependency analysis,
* and parallel scheduling.

### Causal recurrence

A state value may depend on its previous value:

```text
State[t + 1] = F(State[t], Input[t], Parameters)
```

This supports:

* sequence processing,
* memory,
* iterative refinement,
* recurrent computation,
* and stateful control.

### Implicit recurrence

MVALN may also express a fixed-point relation:

```text
State* = F(State*, Input, Parameters)
```

Such a program requires an execution policy, such as:

* maximum iteration count,
* convergence tolerance,
* bounded solver execution,
* monotonic iteration,
* or a termination proof.

---

## Typed values

MVALN values may include:

* scalars,
* vectors,
* matrices,
* tensors,
* Boolean masks,
* symbolic values,
* structured records,
* sequences,
* and persistent state objects.

Every expression has a type:

```text
Type(Expression)
```

Every opcode defines a type-inference rule:

```text
OutputType =
    InferType(
        Opcode,
        Type(A),
        Type(B),
        Type(C),
        Type(D),
        Type(E),
        Attributes
    )
```

Tensor-producing opcodes also define shape inference:

```text
OutputShape =
    InferShape(
        Opcode,
        Shape(A),
        Shape(B),
        Shape(C),
        Shape(D),
        Shape(E),
        Attributes
    )
```

Invalid programs are rejected when:

* operand types are incompatible,
* tensor shapes cannot be reconciled,
* required fields are absent,
* recurrence is undefined,
* or opcode attributes are invalid.

---

## Core opcode set

A compact opcode basis for conventional ANN computation is:

```text
MAP
ZIP
REDUCE
CONTRACT
REINDEX
CONCAT
SELECT
STATE
```

Optional extensions include:

```text
COMPARE
RANDOM
SEARCH
CALL
SOLVE
```

---

## MAP

`MAP` applies a function independently to each element.

```text
Y = MAP(function: f, A: X)
```

Examples:

```text
Y = ReLU(X)
```

```text
Y = exp(X)
```

```text
Y = tanh(X)
```

---

## ZIP

`ZIP` combines corresponding elements from supplied operands.

```text
Y = ZIP(function: f, A: X, B: Y)
```

Examples:

```text
Z = X + Y
```

```text
Z = X × Y
```

```text
Z = max(X, Y)
```

A multi-input form is also valid:

```text
Z = ZIP(
    function: Add,
    A: X₀,
    B: X₁,
    C: X₂,
    D: X₃,
    E: X₄
)
```

Equivalent equation:

```text
Z = X₀ + X₁ + X₂ + X₃ + X₄
```

Any unnecessary field may be omitted.

---

## REDUCE

`REDUCE` combines values along one or more dimensions.

```text
Y = REDUCE(
    function: Sum,
    A: X,
    axes: [1]
)
```

Examples:

```text
Y[i] = Σ X[i, j]
       over j
```

```text
Y[i] = max X[i, j]
       over j
```

```text
Y[i] = mean X[i, j]
       over j
```

---

## CONTRACT

`CONTRACT` performs generalized tensor contraction.

Matrix multiplication is one special case:

```text
Y[i, j] =
    Σ A[i, k] × B[k, j]
    over k
```

MVALN form:

```text
Y = CONTRACT(
    A: X,
    B: W,
    indices: "ik,kj->ij"
)
```

A contraction may use additional operand fields when required.

---

## REINDEX

`REINDEX` changes tensor indexing or arrangement.

```text
Y = REINDEX(
    A: X,
    operation: Transpose
)
```

Supported forms may include:

* transpose,
* reshape,
* slice,
* gather,
* scatter,
* broadcast,
* permutation,
* patch extraction.

---

## CONCAT

`CONCAT` joins supplied values along an axis.

```text
Y = CONCAT(
    A: X₀,
    B: X₁,
    C: X₂,
    axis: 1
)
```

Only supplied fields participate.

---

## SELECT

`SELECT` chooses values according to a condition.

```text
Y = SELECT(
    A: Mask,
    B: TrueValue,
    C: FalseValue
)
```

Equivalent elementwise behavior:

```text
Y[i] =
    TrueValue[i]  when Mask[i] is true
    FalseValue[i] otherwise
```

---

## STATE

`STATE` defines a persistent state transition.

```text
State[t + 1] = STATE(
    A: State[t],
    B: Input[t],
    C: Parameter.W
)
```

This supports recurrent and iterative architectures.

---

## Representation of conventional ANNs

Any conventional ANN expressible as a finite typed tensor graph using the available opcodes can be represented as an MVALN program.

This establishes representational compatibility. It does not establish that every such program can be learned efficiently.

---

## Dense layer

Conventional equation:

```text
Y = f(XW + b)
```

MVALN form:

```text
T₀ = CONTRACT(
    A: X,
    B: W,
    indices: "bi,io->bo"
)

T₁ = ZIP(
    function: Add,
    A: T₀,
    B: b
)

Y = MAP(
    function: f,
    A: T₁
)
```

Nested form:

```text
Y =
    MAP(
        function: f,
        A: ZIP(
            function: Add,
            A: CONTRACT(
                A: X,
                B: W
            ),
            B: b
        )
    )
```

---

## Multilayer perceptron

```text
H₁ = f₁(XW₁ + b₁)

H₂ = f₂(H₁W₂ + b₂)

Y = f₃(H₂W₃ + b₃)
```

General repeated form:

```text
LayerOutput[t + 1] =
    Activation[t](
        LayerOutput[t] × Weight[t]
        + Bias[t]
    )
```

---

## Convolution

A convolution may be decomposed into patch extraction and contraction:

```text
Patches = REINDEX(
    A: X,
    operation: ExtractPatches,
    stride: Stride,
    padding: Padding,
    dilation: Dilation
)

Y = CONTRACT(
    A: Patches,
    B: Kernel
)

Y = ZIP(
    function: Add,
    A: Y,
    B: Bias
)
```

Equivalent abstract equation:

```text
Y = Contract(ExtractPatches(X), Kernel) + Bias
```

---

## Recurrent neural network

Conventional equation:

```text
H[t] =
    tanh(
        X[t]Wₓ
        + H[t - 1]Wₕ
        + b
    )
```

MVALN form:

```text
InputContribution =
    CONTRACT(
        A: X[t],
        B: Wₓ
    )

StateContribution =
    CONTRACT(
        A: H[t - 1],
        B: Wₕ
    )

PreActivation =
    ZIP(
        function: Add,
        A: InputContribution,
        B: StateContribution,
        C: b
    )

H[t] =
    MAP(
        function: tanh,
        A: PreActivation
    )
```

---

## Residual network

Conventional equation:

```text
Y = f(F(X) + X)
```

MVALN form:

```text
Y =
    MAP(
        function: f,
        A: ZIP(
            function: Add,
            A: F(X),
            B: X
        )
    )
```

---

## Attention

```text
Q = XWQ
K = XWK
V = XWV
```

```text
Scores =
    Q × transpose(K)
    / sqrt(d)
    + Mask
```

```text
Probabilities = Softmax(Scores)
```

```text
Y = Probabilities × V
```

MVALN form:

```text
Q = CONTRACT(A: X, B: WQ)

K = CONTRACT(A: X, B: WK)

V = CONTRACT(A: X, B: WV)

KT = REINDEX(
    A: K,
    operation: Transpose
)

RawScores = CONTRACT(
    A: Q,
    B: KT
)

ScaledScores = ZIP(
    function: Divide,
    A: RawScores,
    B: Constant.SqrtDimension
)

MaskedScores = ZIP(
    function: Add,
    A: ScaledScores,
    B: Mask
)

Probabilities = CALL(
    graph: Softmax,
    A: MaskedScores
)

Y = CONTRACT(
    A: Probabilities,
    B: V
)
```

---

## Learning dimensions

MVALN may learn any subset of the following components.

### Opcode selection

```text
Opcode[i] ∈ AvailableOpcodes
```

### Operand binding

```text
Operand[i, field] ∈
    Inputs
    ∪ Parameters
    ∪ States
    ∪ Constants
    ∪ PriorExpressions
    ∪ Omitted
```

### Program topology

The learner may determine:

* expression depth,
* branching structure,
* shared subexpressions,
* skip paths,
* recurrent dependencies,
* and output dependencies.

### Numerical parameters

```text
Θ = {P₀, P₁, ..., Pₙ}
```

MVALN does not prohibit numerical weights.

It removes the requirement that learned weights be the principal representation of intelligence.

### State transitions

The model may learn:

```text
State[t + 1] =
    Program(
        State[t],
        Input[t],
        Parameters
    )
```

### Program length

```text
ProgramLength = number of expressions or instructions
```

A complexity objective may penalize:

```text
ProgramComplexity =
    λ₁ × InstructionCount
    + λ₂ × ExpressionDepth
    + λ₃ × StateSize
    + λ₄ × EstimatedRuntime
```

---

## Structural transformations

A structural learner may modify programs through:

```text
InsertOpcode
DeleteOpcode
ReplaceOpcode
RebindOperand
OmitOperand
RestoreOperand
ShareSubexpression
DuplicateSubexpression
IntroduceState
RemoveState
ChangeAttribute
```

These transformations define the structural search neighborhood.

---

## Training strategies

MVALN does not require one universal training algorithm.

### Alternating optimization

```text
1. Hold the program structure fixed.
2. Optimize numerical parameters.
3. Hold numerical parameters fixed.
4. modify the program structure.
5. Repeat.
```

### Evolutionary search

Programs undergo:

* mutation,
* recombination,
* evaluation,
* selection,
* and complexity regularization.

### Reinforcement learning

A construction policy emits:

```text
Opcode
Operand A
Operand B
Operand C
Operand D
Operand E
Attributes
```

The completed program receives a reward based on:

```text
Reward =
    task performance
    - execution cost
    - memory cost
    - program complexity
```

### Differentiable relaxation

Discrete opcode selection may temporarily become a weighted mixture:

```text
Y =
    p₀ × Opcode₀(X)
    + p₁ × Opcode₁(X)
    + ...
    + pₙ × Opcodeₙ(X)
```

The mixture is later converted into a discrete program.

### Enumerative synthesis

Candidate expressions may be generated and pruned using:

* type constraints,
* shape constraints,
* algebraic equivalence,
* partial evaluation,
* loss bounds,
* and theorem-proving techniques.

### Hybrid optimization

A practical implementation may combine:

```text
discrete structural search
+
continuous parameter optimization
```

---

## Opcode definition

Every opcode should define:

```text
OpcodeDefinition {
    forwardSemantics
    typeInference
    shapeInference
    gradientRule
    executionCost
    sideEffects
}
```

A differentiable opcode may provide a gradient rule.

A nondifferentiable opcode may instead use:

* discrete search,
* surrogate optimization,
* reinforcement learning,
* finite differences,
* symbolic reasoning,
* or local credit assignment.

---

## Execution model

An MVALN program is evaluated as a typed expression graph.

Compilation proceeds through:

```text
program
→ typed graph
→ validated graph
→ optimized graph
→ execution plan
```

Possible compiler transformations include:

* type checking,
* shape inference,
* cycle classification,
* common-subexpression elimination,
* constant folding,
* dead-expression elimination,
* algebraic simplification,
* memory planning,
* and parallel scheduling.

### Stateless inference

```text
Y = Execute(Program, Parameters, Input)
```

### Stateful inference

```text
(Y[t], State[t + 1]) =
    Execute(
        Program,
        Parameters,
        State[t],
        Input[t]
    )
```

---

## Relationship to conventional ANNs

A conventional ANN is one possible MVALN program:

```text
ANN ⊆ MVALN
```

This relationship is representational and depends on the available opcode set.

The conceptual distinction is:

```text
Conventional ANN =
    engineered topology
    + learned coefficients
```

```text
MVALN =
    learned or synthesized topology
    + learned opcode selection
    + learned operand bindings
    + optional learned coefficients
    + persistent program state
```

MVALN may produce a conventional ANN when that is the most effective discovered program.

It may instead produce a model resembling:

* a symbolic expression,
* a state machine,
* a recurrent algorithm,
* a tensor program,
* a decision system,
* a numerical solver,
* or a hybrid architecture.

---

## Proposed advantages

MVALN is intended to investigate:

* explicit computational structure,
* inspectable opcode semantics,
* programmable recurrence,
* direct state representation,
* reusable subexpressions,
* variable program depth,
* architecture discovery,
* conditional execution,
* compact shared computation,
* and symbolic verification.

These are research objectives, not established performance claims.

---

## Principal challenges

### Discrete structural search

Opcode and topology selection create a combinatorial search space.

### Credit assignment

The learner must determine which structural decision caused success or failure.

### Program validity

Structural mutations may create invalid:

* types,
* shapes,
* operand combinations,
* or recurrence.

### Termination

Recursive and recurrent expressions require bounded or provably convergent execution.

### Opcode-vocabulary bias

The available opcode set determines which programs are easy or difficult to discover.

### Mixed optimization domains

Continuous parameter optimization and discrete program optimization require different methods.

### Runtime efficiency

A compact symbolic program is not automatically faster than a conventional tensor graph.

### Empirical validation

MVALN must be compared against established models before superiority claims are justified.

---

## Validation roadmap

### Phase 1: Expression execution

Implement:

* typed expressions,
* optional operand fields,
* opcode registration,
* graph evaluation,
* and deterministic serialization.

### Phase 2: Conventional ANN equivalence

Reproduce:

* dense networks,
* convolutional networks,
* recurrent networks,
* residual networks,
* and attention mechanisms.

### Phase 3: Structural learning

Learn small programs from examples:

```text
Y = A + B
```

```text
Y = A × B + C
```

```text
Y = XOR(A, B)
```

### Phase 4: Joint optimization

Optimize both:

```text
Program structure
```

and:

```text
Numerical parameters
```

### Phase 5: Generalization

Evaluate discovered programs on unseen inputs.

### Phase 6: Ablation

Measure the contribution of:

* opcode learning,
* operand learning,
* recurrence,
* shared subexpressions,
* and numerical parameters.

### Phase 7: Efficiency

Compare:

* parameter count,
* program length,
* runtime,
* memory use,
* training cost,
* inference cost,
* and interpretability.

---

## Reference grammar

```ebnf
Program =
    { Definition },
    OutputExpression ;

Definition =
    Identifier,
    "=",
    Expression ;

Expression =
      InputReference
    | ParameterReference
    | StateReference
    | ConstantReference
    | OpcodeExpression ;

OpcodeExpression =
    OpcodeName,
    "(",
    [ FieldA ],
    [ FieldB ],
    [ FieldC ],
    [ FieldD ],
    [ FieldE ],
    [ Attributes ],
    ")" ;

FieldA = "A:", Expression ;
FieldB = "B:", Expression ;
FieldC = "C:", Expression ;
FieldD = "D:", Expression ;
FieldE = "E:", Expression ;

Attributes =
    ";",
    AttributeList ;

AttributeList =
    Attribute,
    { ",", Attribute } ;
```

Example:

```text
T₀ = CONTRACT(
    A: Input.X,
    B: Parameter.W
)

T₁ = ZIP_ADD(
    A: T₀,
    B: Parameter.b
)

Output = MAP_RELU(
    A: T₁
)
```

Equivalent equation:

```text
Output = ReLU(XW + b)
```

---

## Research hypothesis

The central MVALN hypothesis is:

```text
A learned executable grammar can provide a more general
model class than a fixed neural topology.
```

The architecture should be evaluated by whether it discovers programs that are:

* accurate,
* generalizable,
* computationally efficient,
* compact,
* interpretable,
* and reusable.

MVALN is not defined by artificial neurons.

It is defined by:

```text
opcode composition
+
operand binding
+
state transition
+
program learning
```

---

## Current status

MVALN is a formal architectural proposal.

The following remain to be established experimentally:

* whether useful programs can be learned efficiently,
* which opcode basis produces the best search behavior,
* how structural credit assignment should operate,
* whether MVALN improves sample efficiency,
* whether learned programs generalize beyond their training distribution,
* and whether MVALN can outperform conventional ANNs on practical tasks.

---

## License

No license has been specified.

# TON Opcodes

A decompiler for The Open Network Virtual Machine (TVM) bytecode in Fift assembly.

## Installation

```bash
yarn add @tact-lang/opcode
```

## Usage

For most cases you will want to disassemble a BoC file generated by the Tact/FunC/Tolk compiler.

```typescript
import {AssemblyWriter} from "@tact-lang/opcode"
import {disassembleRoot} from "@tact-lang/opcode"

// Disassemble a source file into a program AST
const program = disassembleRoot(source, {
    computeRefs: false,
})

// Write the program AST into a TVM bytecode string
const res = AssemblyWriter.write(program, {})
console.log(res)
```

If you want to decompile BoC file with non-standard root layout (for example, wallet v1), you can do the following:

```typescript
import {AssemblyWriter} from "@tact-lang/opcode"
import {disassembleRawRoot} from "@tact-lang/opcode"

const program = disassembleRawRoot(source)

const res = AssemblyWriter.write(program, {})
console.log(res)
```

If you want to disassemble a single Cell into an array of opcodes, you can do the following:

```typescript
import {disassemble} from "@tact-lang/opcode"

const opcodes = disassemble({source: cell})
```

## Thanks to

- [Steve Korshakov](https://github.com/ex3ndr)
- [Nick Nekilov](https://github.com/NickNekilov)
- [Vladimir Lebedev](https://github.com/hacker-volodya)

## License

MIT

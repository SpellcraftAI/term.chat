# llmshell

`llmshell` is a programmable terminal integration for OpenAI and Anthropic
models, with support for adding custom examples and tools.

## Installing

To install from the latest release, run:

```sh
curl https://readme.llmshell.com/install | bash
```

This will install from `llmshell.tar.gz` and add to your system PATH. 

## Uninstalling
Use `~/llmshell/uninstall.sh` to uninstall and remove from your system PATH.

## Usage

Once you've installed the program, you can use it by running `llmshell`.

### Adding custom tools

First, install `ai` and `zod` into your llmshell config directory:

```sh
cd ~/.config/llmshell && bun i ai zod
```

You can then define your custom tools:

```ts
// ~/.config/llmshell/tools.ts
import { tool, type CoreTool } from "ai"
import { z } from "zod"

export default {
  sayHello: tool({
    description: "Say hello to the user.",
    parameters: z.object({
      name: z.string().describe("The name of the user to greet.")
    }),
    execute: async ({ name }) => {
      return `Hello, ${name}!`
    }
  })
} satisfies Record<string, CoreTool>
```

### Adding custom examples

Custom examples are loaded from `~/.config/llmshell/examples/*.jsonl`.

## Source code

If you buy a license at [llmshell.com](https://llmshell.com), you will receive
the source code under a source available license, which does not allow
redistribution or copying. This project will be released under MIT License in
the future.
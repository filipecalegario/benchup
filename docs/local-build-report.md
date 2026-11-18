# Registro de build local: BenchUp no macOS

Em 18/11/2026, o BenchUp foi compilado e executado com sucesso a partir do código-fonte deste repositório, numa máquina macOS que até então não tinha Rust instalado.

## Ambiente

| Item | Versão |
| --- | --- |
| Sistema | macOS 15.6.1 (arm64, Apple M3 Pro) |
| Rust | rustc 1.100.0 (0ef1bc386 2026-11-09) |
| Cargo | cargo 1.100.0 (3acc79c0c 2026-11-05) |
| Compilador C/C++ | Apple clang 17.0.0 (Xcode Command Line Tools) |
| Commit | `64b2a44` (branch `main`, versão 0.6.6 do workspace) |

## Passos

1. Confirmar que as Xcode Command Line Tools estão instaladas (`xcode-select -p` retornou `/Library/Developer/CommandLineTools`).

2. Instalar o Rust via rustup, com o perfil mínimo:

   ```sh
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y --profile minimal
   source ~/.cargo/env
   ```

3. Compilar o app desktop:

   ```sh
   cargo build -p benchup-app
   ```

4. Executar:

   ```sh
   cargo run -p benchup-app
   ```

## Resultado

A compilação inicial, com todas as dependências, terminou sem erros em cerca de 2 minutos e 32 segundos (perfil `dev`). A execução seguinte recompilou só o crate `benchup-app`, em uns 20 segundos, e abriu o app.

A janela "BenchUp, 3D workspace" abriu normalmente com o modelo vazio. Estavam visíveis a barra de ferramentas (Select, Line, Erase, Orbit, Push/Pull, Scale, Offset, Move, Rotate, Paint, Dimensions), o viewport 3D com grid e eixos, e o painel lateral (Properties, Outliner, Units, Components, Tags, Display, View, Time & Cost Estimates). O log não registrou erros durante a execução. Quando a janela foi fechada manualmente, o processo terminou com código de saída 0.

## Limitações deste registro

Este teste confirma que o projeto compila e que o app desktop abre e encerra corretamente. As ferramentas de modelagem, a importação e exportação de arquivos, a geração de PDF e a versão web (WebAssembly via `trunk`) não foram testadas. A suíte de testes (`cargo test`) também não foi executada.

## Observação sobre o repositório

Os links de download e a demo web que aparecem no README apontam para `BenchUp3D/editor`, que não estava acessível no momento do teste. Por isso, compilar a partir do código foi o único caminho verificado para rodar o app.

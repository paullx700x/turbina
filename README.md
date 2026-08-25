# Turbina

Laboratório de computação no navegador que compara JavaScript na CPU com um **compute shader WebGPU em WGSL**.

## O benchmark

A mesma soma de dois vetores `Float32Array` é executada em CPU e GPU. A medição GPU é ponta a ponta para a operação: criação/upload dos buffers, compilação/pipeline, dispatch e leitura do resultado. Isso é proposital para não esconder o overhead de usar a GPU.

Quando CPU e GPU são executadas juntas, o resultado GPU é comparado com o resultado da CPU. O status só mostra `verificado ✓` se o checksum estiver dentro da tolerância.

## Recursos

- tamanho de carga configurável;
- benchmark CPU em JavaScript puro;
- compute pipeline WebGPU;
- validação dos erros de compilação WGSL quando a API oferece `getCompilationInfo()`;
- checksum e validação CPU/GPU;
- throughput em itens/s;
- histórico visual;
- tratamento de `GPUDevice.lost`;
- detecção e fallback quando WebGPU não existe.

## Autoteste

Abra o console do navegador e execute:

```js
await TurbinaSelfTest()
```

Em navegador com WebGPU, o teste cria vetores pequenos, compila o WGSL, despacha o compute shader, faz readback e compara cada valor com a soma calculada na CPU. Em navegador sem WebGPU ele retorna `gpuSkipped: true` em vez de fingir que a GPU foi testada.

## Compatibilidade

WebGPU depende do navegador, sistema operacional, driver e adaptador. Se `navigator.gpu` não existir ou nenhum adaptador puder ser criado, a parte CPU continua funcionando normalmente e a interface informa a indisponibilidade.

## Licença

MIT.

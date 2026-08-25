# Turbina

Laboratório de computação no navegador que compara JavaScript na CPU com um **compute shader WebGPU em WGSL**.

## O benchmark

A mesma soma de dois vetores `Float32Array` é executada em CPU e GPU. A medição da GPU inclui criação/transferência de buffers, dispatch e leitura do resultado — propositalmente, para não mascarar overhead.

## Recursos
- tamanho de carga configurável;
- CPU benchmark;
- WebGPU compute pipeline;
- checksum para conferir resultado;
- throughput em itens/s;
- histórico visual;
- detecção e fallback quando WebGPU não existe.

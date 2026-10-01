# Atualizador do Emissor Nacional Rocha

## Arquitetura valida a partir da v0.11.3

O atualizador deve distribuir sempre o aplicativo completo. Nao usar patch que dependa de arquivo .bak como programa principal.

Fluxo:
1. verificar version.json;
2. baixar o pacote completo;
3. validar SHA-256;
4. gravar como EmissorNacionalRocha.jar.new;
5. iniciar um processo atualizador externo;
6. copiar a versao atual para .bak;
7. substituir o JAR principal;
8. iniciar a nova versao com health-check;
9. se o health-check falhar, restaurar automaticamente o .bak e reiniciar a versao anterior.

A versao v0.11.3 inclui o UpdateBootstrap separado do processo principal e o marcador de health-check de inicializacao.

## Regra de publicacao

O version.json so deve ser alterado para uma versao nova depois que:
- o pacote completo estiver publicado;
- o SHA-256 tiver sido conferido;
- o JAR tiver sido validado como executavel;
- o ciclo de atualizacao e rollback tiver sido testado.

Enquanto nao houver release completo validado, o canal deve permanecer pausado.

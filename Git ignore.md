#git #Boilerplate 

[[Git]] ignore é um arquivo oculto dentro de um diretório local que lista arquivos, pastas e extensões para serem excluídas de um pedido de push/pull

# Modelo
```
# Código fonte compilado #
###################
*.com
*.class
*.dll
*.exe
*.o
*.so

# Pacotes #
############
# é melhor abrir esses arquivos e commitar o código fonte cru
# git tem seus próprios métodos de compressão
*.7z
*.dmg
*.gz
*.iso
*.jar
*.rar
*.tar
*.zip

# Logs e banco de dados #
######################
*.log
*.sql
*.sqlite

# Arquivos gerados por Sistema Operacional
######################
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db
```


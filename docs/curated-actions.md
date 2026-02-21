# Lista Curada de GitHub Actions para MEVN

Esta é uma coleção de GitHub Actions recomendadas para projetos usando a stack MEVN (MongoDB, Express, Vue, Node.js).

## ⚙️ Continuous Integration (CI)

### Core Actions
- **[actions/checkout](https://github.com/actions/checkout)** (v4)
  - Padrão para fazer checkout do código do repositório
  - Essencial em praticamente todos os workflows
  
- **[actions/setup-node](https://github.com/actions/setup-node)** (v4)
  - Configura versões específicas do Node.js
  - Suporta cache automático de dependências npm/yarn/pnpm
  - Exemplo: Node 18, 20, ou LTS

### Linting & Code Quality
- **[wearerequired/lint-action](https://github.com/wearerequired/lint-action)**
  - Roda ESLint automaticamente e comenta nos PRs
  - Suporta auto-fix de problemas de lint
  
- **[reviewdog/action-eslint](https://github.com/reviewdog/action-eslint)**
  - Integra ESLint com revisão de código
  - Adiciona anotações inline nos PRs

### Testing
- **[ArtiomTr/jest-coverage-report-action](https://github.com/ArtiomTr/jest-coverage-report-action)**
  - Roda Jest e gera relatórios de cobertura
  - Comenta resultados diretamente no PR
  
- **[cypress-io/github-action](https://github.com/cypress-io/github-action)** (v6)
  - Testes end-to-end para Vue frontend
  - Suporta gravação de vídeos e screenshots
  - Pode rodar testes em paralelo

- **[mattallty/jest-github-action](https://github.com/mattallty/jest-github-action)**
  - Action simplificada para rodar testes Jest
  - Integração nativa com GitHub Checks

## 🛠 Build

### Caching
- **[actions/cache](https://github.com/actions/cache)** (v4)
  - Cache de `node_modules` para builds mais rápidos
  - Reduz tempo de instalação em até 80%
  - Suporte para npm, yarn, pnpm

### Vue Build
- **Script customizado com `npm run build`**
  - Para projetos Vue CLI ou Vite
  - Compatível com vue.config.js ou vite.config.js
  
- **[JamesIves/github-pages-deploy-action](https://github.com/JamesIves/github-pages-deploy-action)**
  - Faz build e deploy em uma única action
  - Ideal para SPAs Vue

### Docker
- **[docker/setup-buildx-action](https://github.com/docker/setup-buildx-action)** (v3)
  - Configura Docker Buildx para builds avançados
  
- **[docker/build-push-action](https://github.com/docker/build-push-action)** (v5)
  - Build e push de imagens Docker
  - Suporta multi-platform builds
  - Cache layers para otimização

- **[docker/login-action](https://github.com/docker/login-action)** (v3)
  - Login em registries (Docker Hub, GHCR, etc)

## 🚀 Deployment

### Static Site Hosting
- **[peaceiris/actions-gh-pages](https://github.com/peaceiris/actions-gh-pages)** (v3)
  - Deploy Vue frontend para GitHub Pages
  - Suporta custom domains e CNAME
  - Força HTTPS automaticamente

### Platform as a Service (PaaS)
- **[akhileshns/heroku-deploy](https://github.com/akhileshns/heroku-deploy)** (v3.13.15)
  - Deploy para Heroku
  - Suporta variáveis de ambiente
  - Ideal para backend Node/Express

- **[amondnet/vercel-action](https://github.com/amondnet/vercel-action)** (v25)
  - Deploy para Vercel
  - Perfeito para Vue SPAs
  - Preview automático de PRs

- **API Deploy para Render**
  - Via `curl` com Render API
  - Webhook triggers para deploys automáticos

### SSH Deploy
- **[appleboy/ssh-action](https://github.com/appleboy/ssh-action)**
  - Deploy via SSH para VPS ou servidores dedicados
  - Útil para ambientes self-hosted

### FTP/SFTP Deploy
- **[SamKirkland/FTP-Deploy-Action](https://github.com/SamKirkland/FTP-Deploy-Action)** (v4.3.5)
  - Deploy via FTP/SFTP
  - Para hospedagem compartilhada

## 🔒 Security

### Vulnerability Scanning
- **[github/codeql-action](https://github.com/github/codeql-action)** (v3)
  - Análise estática de segurança
  - Suporta JavaScript e TypeScript
  - Detecta vulnerabilidades como SQL injection, XSS
  
- **[snyk/actions](https://github.com/snyk/actions)**
  - Verifica vulnerabilidades em dependências npm
  - Monitora Docker images
  - Integra com Snyk dashboard

### Dependency Management
- **[dependabot](https://docs.github.com/en/code-security/dependabot)**
  - Nativo do GitHub (configurado via `.github/dependabot.yml`)
  - Atualização automática de dependências
  - Cria PRs para updates de segurança

- **[ossf/scorecard-action](https://github.com/ossf/scorecard-action)**
  - Avalia práticas de segurança do projeto
  - Score OpenSSF

### Node.js Specific
- **[actions/setup-node com check-latest](https://github.com/actions/setup-node)**
  - Use `check-latest: true` para garantir versão mais recente e segura
  
- **Script customizado com `npm audit`**
  - Roda `npm audit --audit-level=high` no CI
  - Falha se encontrar vulnerabilidades críticas

### Secret Scanning
- **[trufflesecurity/trufflehog](https://github.com/trufflesecurity/trufflehog)**
  - Detecta secrets commitados acidentalmente
  - Verifica histórico completo do Git

## 📊 Monitoring & Reporting

### Coverage
- **[codecov/codecov-action](https://github.com/codecov/codecov-action)** (v4)
  - Upload de relatórios de cobertura para Codecov
  - Badges e gráficos de tendência

### Notifications
- **[8398a7/action-slack](https://github.com/8398a7/action-slack)**
  - Notificações de build no Slack
  - Customizável com webhooks

## 🎯 Exemplo de Workflow Completo

```yaml
name: MEVN Full Pipeline

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  ci:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      
      - run: npm ci
      
      - uses: reviewdog/action-eslint@v1
        with:
          reporter: github-pr-review
      
      - uses: ArtiomTr/jest-coverage-report-action@v2
      
      - uses: cypress-io/github-action@v6
        with:
          start: npm run dev
          wait-on: 'http://localhost:5173'

  security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - uses: github/codeql-action/init@v3
        with:
          languages: javascript
      
      - uses: github/codeql-action/analyze@v3
      
      - uses: snyk/actions/node@master
        env:
          SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}

  build:
    runs-on: ubuntu-latest
    needs: [ci, security]
    steps:
      - uses: actions/checkout@v4
      
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      
      - run: npm ci
      - run: npm run build
      
      - uses: actions/upload-artifact@v4
        with:
          name: dist
          path: dist/

  deploy:
    runs-on: ubuntu-latest
    needs: build
    if: github.ref == 'refs/heads/main'
    steps:
      - uses: actions/checkout@v4
      
      - uses: actions/download-artifact@v4
        with:
          name: dist
          path: dist
      
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

## 🔗 Recursos Adicionais

- [GitHub Actions Marketplace](https://github.com/marketplace?type=actions)
- [Awesome Actions](https://github.com/sdras/awesome-actions)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

## 💡 Dicas de Uso

1. **Sempre fixe versões**: Use `@v4` em vez de `@latest` para estabilidade
2. **Use cache**: Configure `actions/cache` ou `cache: 'npm'` no setup-node
3. **Paralelização**: Separe jobs independentes para rodar em paralelo
4. **Condicionais**: Use `if:` para controlar quando jobs devem rodar
5. **Secrets**: Nunca commite tokens, use GitHub Secrets
6. **Matrix strategy**: Teste em múltiplas versões do Node (16, 18, 20)

## 🎨 Badges para README

```markdown
<img src="https://github.com/el-backendev/mevn-actions/workflows/CI%20Pipeline/badge.svg">
<img src="https://github.com/el-backendev/mevn-actions/workflows/Security%20Analysis/badge.svg">
<img src="https://github.com/el-backendev/mevn-actions/workflows/Deploy%20Workflow/badge.svg">
```

---

**Última atualização**: 2026-02-12

# GRIB - Setup para José Folha

## Comandos com Caminhos Completos

### 1. Navegar para o Projeto
```powershell
cd "C:\Users\José Folha\Desktop\grib-project\grib-project"
```

### 2. Setup Backend
```powershell
cd "C:\Users\José Folha\Desktop\grib-project\grib-project\backend"
npm install
npx prisma db push
npx prisma generate
```

### 3. Setup Frontend
```powershell
cd "C:\Users\José Folha\Desktop\grib-project\grib-project\frontend"
npm install
```

### 4. Executar o Projeto

**Terminal 1 - Backend:**
```powershell
cd "C:\Users\José Folha\Desktop\grib-project\grib-project\backend"
npm run dev
```

**Terminal 2 - Frontend:**
```powershell
cd "C:\Users\José Folha\Desktop\grib-project\grib-project\frontend"
npm run dev
```

### 5. Adicionar Jogadores (Opcional)
```powershell
cd "C:\Users\José Folha\Desktop\grib-project\grib-project\backend"
npx prisma studio
```

### 6. URLs para Testar
- Website: http://localhost:5173
- API: http://localhost:3002/api/players
- Health: http://localhost:3002/health

## Se Algo Falhar

**Erro de porta ocupada:**
```powershell
taskkill /f /im node.exe
```

**Erro EPERM Prisma (mais comum):**
```powershell
cd "C:\Users\José Folha\Desktop\grib-project\grib-project\backend"
taskkill /f /im node.exe
rmdir /s node_modules\.prisma
npx prisma generate
npm run dev
```

**API retorna 500 Error:**
```powershell
cd "C:\Users\José Folha\Desktop\grib-project\grib-project\backend"
npx prisma generate
npm run dev
```

**Proxy não funciona (fetch erro):**
```powershell
cd "C:\Users\José Folha\Desktop\grib-project\grib-project\frontend"
# Para o frontend (Ctrl+C)
npm run dev
```

**Recriar base de dados:**
```powershell
cd "C:\Users\José Folha\Desktop\grib-project\grib-project\backend"
npx prisma db push --force-reset
```

**Reinstalar tudo (último recurso):**
```powershell
# Backend
cd "C:\Users\José Folha\Desktop\grib-project\grib-project\backend"
rmdir /s node_modules
npm install
npx prisma generate

# Frontend  
cd "C:\Users\José Folha\Desktop\grib-project\grib-project\frontend"
rmdir /s node_modules
npm install
```

**Verificar se está tudo a funcionar:**
1. Backend: http://localhost:3001/health deve mostrar `{"status":"OK"...}`
2. API: http://localhost:3001/api/players deve mostrar `[]`
3. Frontend: http://localhost:5173 deve mostrar página GRIB
4. No console do browser: `fetch('/api/players').then(r=>r.json()).then(console.log)` deve mostrar `[]`

## Ordem de Resolução de Problemas
1. Mata todos os processos Node: `taskkill /f /im node.exe`
2. Regenera Prisma: `npx prisma generate`
3. Reinicia backend: `npm run dev`
4. Testa: http://localhost:3001/health
5. Se funcionar, reinicia frontend: `npm run dev`
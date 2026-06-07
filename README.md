<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>Rádio Net</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=DM+Mono:wght@400&family=DM+Sans:wght@400;500&display=swap" rel="stylesheet">
<style>
:root{--bg:#0a0f1e;--sf:#111827;--sf2:#1a2236;--bd:#1e2d45;--ac:#00d4ff;--ac2:#0088cc;--gn:#00e676;--yw:#ffd600;--rd:#ff4444;--tx:#e8f0fe;--mu:#607090}
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--tx);min-height:100vh;display:flex;flex-direction:column}

/* LOGIN */
#ls{position:fixed;inset:0;z-index:9999;background:var(--bg);display:flex;align-items:center;justify-content:center;padding:16px}
.lb{width:100%;max-width:380px;background:var(--sf);border:1px solid var(--bd);border-radius:20px;padding:28px;box-shadow:0 20px 60px rgba(0,0,0,.7)}
.ll{text-align:center;margin-bottom:20px}
.ll-logo{font-family:'Syne',sans-serif;font-size:32px;font-weight:800;letter-spacing:-1px}
.ll-logo span{color:var(--ac)}
.ll-sub{font-size:13px;color:var(--mu);margin-top:4px}
.ll-icon{font-size:48px;margin-bottom:8px}
.lt{display:flex;background:var(--bg);border:1px solid var(--bd);border-radius:10px;padding:3px;gap:3px;margin-bottom:18px}
.lt button{flex:1;padding:9px;border:none;border-radius:8px;background:transparent;color:var(--mu);font-family:'DM Sans',sans-serif;font-size:13px;font-weight:500;cursor:pointer}
.lt button.on{background:linear-gradient(135deg,var(--ac2),var(--ac));color:#000;font-weight:700}
.lf{margin-bottom:12px}
.lf label{display:block;font-size:11px;font-weight:600;color:var(--mu);margin-bottom:5px;text-transform:uppercase;letter-spacing:.6px}
.lf input{width:100%;background:var(--bg);border:1px solid var(--bd);border-radius:8px;padding:11px 13px;color:var(--tx);font-family:'DM Sans',sans-serif;font-size:14px;outline:none}
.lf input:focus{border-color:var(--ac)}
.lbtn{width:100%;padding:13px;border-radius:10px;border:none;background:linear-gradient(135deg,var(--ac2),var(--ac));color:#000;font-family:'DM Sans',sans-serif;font-size:15px;font-weight:700;cursor:pointer;margin-top:6px}
.lerr{background:rgba(255,68,68,.12);border:1px solid rgba(255,68,68,.3);border-radius:8px;padding:9px 13px;font-size:13px;color:var(--rd);margin-bottom:12px;display:none;text-align:center}
.lhint{text-align:center;margin-top:10px;font-size:12px;color:var(--mu)}

/* HEADER */
header{background:var(--sf);border-bottom:1px solid var(--bd);padding:0 18px;height:56px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:100}
.logo{font-family:'Syne',sans-serif;font-weight:800;font-size:18px;display:flex;align-items:center;gap:7px}
.lic{width:28px;height:28px;background:linear-gradient(135deg,var(--ac),var(--ac2));border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:13px}
.logo span{color:var(--ac)}
.hs{display:flex;align-items:center;gap:10px}
.hst{font-size:12px;color:var(--mu)}
.hst b{color:var(--tx);font-family:'DM Mono',monospace}
.ub{display:flex;align-items:center;gap:6px;background:rgba(0,212,255,.08);border:1px solid rgba(0,212,255,.2);border-radius:20px;padding:4px 11px;font-size:12px;cursor:pointer}
.ur{font-size:10px;color:var(--mu);text-transform:uppercase}

/* LAYOUT */
.app{display:flex;flex:1}
nav{width:190px;background:var(--sf);border-right:1px solid var(--bd);padding:12px 8px;display:flex;flex-direction:column;gap:2px;flex-shrink:0}
.nl{font-size:10px;font-weight:600;letter-spacing:1.4px;color:var(--mu);padding:8px 8px 4px;text-transform:uppercase}
.nb{display:flex;align-items:center;gap:7px;padding:9px 10px;border-radius:8px;border:none;background:transparent;color:var(--mu);font-size:13px;font-family:'DM Sans',sans-serif;cursor:pointer;text-align:left;width:100%}
.nb:hover{background:var(--sf2);color:var(--tx)}
.nb.on{background:rgba(0,212,255,.12);color:var(--ac)}
.ic{font-size:14px;width:16px;text-align:center}
main{flex:1;padding:20px;overflow-y:auto}
.page{display:none}.page.on{display:block}
.ph{display:flex;align-items:center;justify-content:space-between;margin-bottom:20px;flex-wrap:wrap;gap:8px}
.pt{font-family:'Syne',sans-serif;font-size:22px;font-weight:700}
.ps{color:var(--mu);font-size:13px;margin-top:2px}
.card{background:var(--sf);border:1px solid var(--bd);border-radius:12px;padding:16px;margin-bottom:12px}
.ct{font-family:'Syne',sans-serif;font-size:13px;font-weight:700;margin-bottom:12px;color:var(--ac)}
.g2{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.g3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px}
.g4{display:grid;grid-template-columns:repeat(4,1fr);gap:12px}
.sc{background:var(--sf);border:1px solid var(--bd);border-radius:12px;padding:14px}
.sl{font-size:11px;color:var(--mu);margin-bottom:5px;text-transform:uppercase;letter-spacing:.6px}
.sv{font-family:'DM Mono',monospace;font-size:22px;font-weight:500}
.sv.bl{color:var(--ac)}.sv.gn{color:var(--gn)}.sv.yw{color:var(--yw)}
.fg{margin-bottom:11px}
.fg label{display:block;font-size:11px;font-weight:500;color:var(--mu);margin-bottom:4px;text-transform:uppercase;letter-spacing:.5px}
.fg input,.fg select,.fg textarea{width:100%;background:var(--bg);border:1px solid var(--bd);border-radius:8px;padding:9px 12px;color:var(--tx);font-family:'DM Sans',sans-serif;font-size:13px;outline:none}
.fg input:focus,.fg select:focus{border-color:var(--ac)}
.fg select option{background:var(--sf)}
.sec{font-size:11px;font-weight:600;letter-spacing:1px;text-transform:uppercase;color:var(--ac);margin:12px 0 8px;padding-bottom:4px;border-bottom:1px solid var(--bd)}
.btn{padding:8px 14px;border-radius:8px;border:none;font-family:'DM Sans',sans-serif;font-size:12px;font-weight:500;cursor:pointer;display:inline-flex;align-items:center;gap:4px}
.bp{background:var(--ac);color:#000}
.br{background:var(--rd);color:#fff}
.bg2{background:var(--sf2);color:var(--tx);border:1px solid var(--bd)}
.bs{padding:5px 9px;font-size:11px}
.bgn{background:var(--gn);color:#000}
.bor{background:#ff9100;color:#000}
.tw{overflow-x:auto}
table{width:100%;border-collapse:collapse;font-size:12px}
thead th{text-align:left;padding:7px 11px;font-size:10px;font-weight:600;color:var(--mu);text-transform:uppercase;border-bottom:1px solid var(--bd)}
tbody tr{border-bottom:1px solid var(--bd)}
tbody tr:hover{background:var(--sf2)}
tbody td{padding:9px 11px}
.bx{display:inline-block;padding:2px 8px;border-radius:20px;font-size:11px;font-weight:600}
.bgn2{background:rgba(0,230,118,.15);color:var(--gn)}
.brd{background:rgba(255,68,68,.15);color:var(--rd)}
.byw{background:rgba(255,214,0,.15);color:var(--yw)}
.bbl{background:rgba(0,212,255,.15);color:var(--ac)}
.sw{position:relative;width:200px}
.sw input{width:100%;background:var(--sf2);border:1px solid var(--bd);border-radius:8px;padding:7px 11px 7px 30px;color:var(--tx);font-family:'DM Sans',sans-serif;font-size:13px;outline:none}
.si{position:absolute;left:8px;top:50%;transform:translateY(-50%);color:var(--mu);font-size:12px}
.mo{display:none;position:fixed;inset:0;background:rgba(0,0,0,.7);z-index:200;align-items:center;justify-content:center;padding:14px}
.mo.on{display:flex}
.md{background:var(--sf);border:1px solid var(--bd);border-radius:16px;width:100%;max-width:560px;max-height:90vh;overflow-y:auto;padding:22px}
.mh{display:flex;justify-content:space-between;align-items:center;margin-bottom:16px}
.mt{font-family:'Syne',sans-serif;font-size:15px;font-weight:700}
.mc{background:none;border:none;color:var(--mu);font-size:20px;cursor:pointer;line-height:1}
.mft{display:flex;gap:8px;justify-content:flex-end;margin-top:16px}
.fx{display:flex;align-items:center;gap:8px}
.dv{border:none;border-top:1px solid var(--bd);margin:12px 0}
.empty{text-align:center;padding:32px 16px;color:var(--mu)}
.ei{font-size:32px;margin-bottom:8px}
#toast{position:fixed;bottom:18px;right:18px;background:var(--sf2);border:1px solid var(--bd);border-radius:10px;padding:11px 15px;font-size:13px;z-index:400;transform:translateY(60px);opacity:0;transition:all .25s}
#toast.on{transform:translateY(0);opacity:1}
#toast.ok{border-color:var(--gn)}
#toast.er{border-color:var(--rd)}
.fi{background:var(--sf2);border:1px solid var(--bd);border-radius:10px;padding:12px 14px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:6px;margin-bottom:7px}
.fi h4{font-size:13px;font-weight:500;margin-bottom:2px}
.fi p{font-size:11px;color:var(--mu)}
.fv{font-family:'DM Mono',monospace;font-size:16px;color:var(--ac)}
.wc{background:linear-gradient(135deg,rgba(0,136,204,.2),rgba(0,212,255,.05));border:1px solid rgba(0,212,255,.2);border-radius:12px;padding:16px;margin-bottom:9px}
.pt2{display:inline-flex;align-items:center;gap:3px;background:rgba(0,212,255,.12);border:1px solid rgba(0,212,255,.2);border-radius:20px;padding:2px 9px;font-size:11px;font-weight:600;color:var(--ac)}
.ec{background:var(--sf2);border:1px solid var(--bd);border-radius:10px;padding:13px;margin-bottom:8px}
.ipb{font-family:'DM Mono',monospace;background:rgba(0,212,255,.1);border:1px solid rgba(0,212,255,.2);color:var(--ac);border-radius:5px;padding:1px 6px;font-size:11px}
.ir{display:flex;justify-content:space-between;align-items:center;padding:5px 0;border-bottom:1px solid rgba(255,255,255,.05);font-size:12px}
.ir:last-child{border:none}
.lb2{color:var(--mu)}
.vl{font-family:'DM Mono',monospace;font-size:11px}
.pcw{max-width:460px;margin:0 auto}
.pcc{background:linear-gradient(160deg,rgba(0,136,204,.12),rgba(0,212,255,.03));border:1px solid rgba(0,212,255,.18);border-radius:16px;padding:22px}
.pch{text-align:center;margin-bottom:18px}
.pch h2{font-family:'Syne',sans-serif;font-size:18px;font-weight:800;margin-top:4px}
.pch p{color:var(--mu);font-size:12px}
.pcinfo{background:rgba(0,230,118,.06);border:1px solid rgba(0,230,118,.16);border-radius:10px;padding:13px;margin-bottom:13px}
.pcinfo h3{font-family:'Syne',sans-serif;font-size:13px;margin-bottom:10px;color:var(--gn)}
.eqc{background:rgba(0,212,255,.04);border:1px solid rgba(0,212,255,.13);border-radius:10px;padding:12px;margin-bottom:8px}
.spw{cursor:pointer;user-select:none;font-size:12px;color:var(--mu)}
.spw .tl{font-size:11px;color:var(--ac)}
</style>
</head>
<body>

<div id="ls" style="position:fixed;top:0;left:0;right:0;bottom:0;z-index:9999;background:#0a0f1e;display:flex;align-items:center;justify-content:center;padding:16px">
<div class="lb">
  <div class="ll">
    <img src="data:image/jpeg;base64,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" alt="Rádio Net" style="width:240px;max-width:100%;border-radius:8px;margin-bottom:4px">
    <div class="ll-sub">Sistema de Gestão</div>
  </div>
  <div class="lt">
    <button id="t0" class="on" onclick="setTab(0)">👔 CEO / Colaborador</button>
    <button id="t1" onclick="setTab(1)">👤 Cliente</button>
  </div>
  <div class="lerr" id="lerr"></div>
  <div id="fa">
    <div class="lf"><label>Usuário</label><input id="au" placeholder="Seu usuário" autocomplete="username"></div>
    <div class="lf"><label>Senha</label><input id="ap" type="password" placeholder="••••••••"></div>
    <button class="lbtn" onclick="lAdm()">🔐 Entrar no Sistema</button>
  </div>
  <div id="fc" style="display:none">
    <div class="lf"><label>CPF / CNPJ</label><input id="cu" placeholder="000.000.000-00"></div>
    <div class="lf"><label>Senha</label><input id="cp" type="password" placeholder="Últimos 4 dígitos do CPF"></div>
    <button class="lbtn" onclick="lCli()">🔑 Acessar Minha Conta</button>
    <div class="lhint">Senha: últimos 4 dígitos do CPF</div>
  </div>
</div>
</div>

<header style="display:none" id="main-header">
  <div class="logo"><div class="lic">📡</div>Rádio <span>Net</span></div>
  <div class="hs" id="hs">
    <div class="hst">Clientes: <b id="h1">0</b></div>
    <div class="hst">Ativos: <b id="h2" style="color:var(--gn)">0</b></div>
    <div class="hst">Receita: <b id="h3" style="color:var(--ac)">R$0</b></div>
    <div class="ub" onclick="sair()"><span id="hnm">—</span> <span class="ur" id="hrl">—</span> <span style="color:var(--rd)">⏏</span></div>
  </div>
</header>

<div class="app" id="main-app" style="display:none">
<nav id="nav">
  <div class="nl">Menu</div>
  <button class="nb on" data-p="dashboard" onclick="go('dashboard',this)"><span class="ic">🏠</span>Dashboard</button>
  <button class="nb" data-p="clientes" onclick="go('clientes',this)"><span class="ic">👥</span>Clientes</button>
  <button class="nb" data-p="equipamentos" onclick="go('equipamentos',this)"><span class="ic">🖥️</span>Equipamentos</button>
  <button class="nb" data-p="planos" onclick="go('planos',this)"><span class="ic">⚡</span>Planos</button>
  <button class="nb" data-p="redes" onclick="go('redes',this)"><span class="ic">📶</span>Redes Wi-Fi</button>
  <button class="nb" data-p="faturas" onclick="go('faturas',this)"><span class="ic">💰</span>Faturas</button>
</nav>
<main>

<div id="page-dashboard" class="page on">
  <div class="ph"><div><div class="pt">Dashboard</div><div class="ps">Visão geral</div></div></div>
  <div class="g4" id="ds"></div>
  <div class="g2" style="margin-top:12px">
    <div class="card"><div class="ct">📋 Últimos clientes</div><div id="dcl"></div></div>
    <div class="card"><div class="ct">💳 Faturas próximas</div><div id="dft"></div></div>
  </div>
</div>

<div id="page-clientes" class="page">
  <div class="ph">
    <div><div class="pt">Clientes</div><div class="ps">Gerencie clientes</div></div>
    <div class="fx"><div class="sw"><span class="si">🔍</span><input id="sc" placeholder="Buscar…" oninput="rCli()"></div>
    <button class="btn bp" onclick="oCli()">＋ Novo</button></div>
  </div>
  <div class="card"><div class="tw">
    <table><thead><tr><th>Nome</th><th>CPF</th><th>Telefone</th><th>Plano</th><th>Venc.</th><th>Status</th><th>Ações</th></tr></thead>
    <tbody id="tcl"></tbody></table>
    <div id="ecl" class="empty" style="display:none"><div class="ei">👥</div>Nenhum cliente.</div>
  </div></div>
</div>

<div id="page-equipamentos" class="page">
  <div class="ph">
    <div><div class="pt">Equipamentos</div><div class="ps">Roteadores dos clientes</div></div>
    <div class="fx"><div class="sw"><span class="si">🔍</span><input id="se" placeholder="Buscar…" oninput="rEq()"></div>
    <button class="btn bp" onclick="oEq()">＋ Novo</button></div>
  </div>
  <div id="leq"></div>
</div>

<div id="page-planos" class="page">
  <div class="ph"><div><div class="pt">Planos</div><div class="ps">Planos de internet</div></div>
  <button class="btn bp" onclick="oM('m-pl')">＋ Novo</button></div>
  <div class="g3" id="gpl"></div>
</div>

<div id="page-redes" class="page">
  <div class="ph"><div><div class="pt">Redes Wi-Fi</div><div class="ps">Pontos de acesso</div></div>
  <button class="btn bp" onclick="oM('m-rd')">＋ Nova</button></div>
  <div id="lrd"></div>
</div>

<div id="page-faturas" class="page">
  <div class="ph">
    <div><div class="pt">Faturas</div><div class="ps">Controle financeiro</div></div>
    <div class="fx">
      <select id="ffl" onchange="rFat()" style="background:var(--sf2);border:1px solid var(--bd);border-radius:8px;padding:7px 11px;color:var(--tx);font-size:12px;outline:none">
        <option value="todos">Todas</option><option value="pendente">Pendentes</option><option value="pago">Pagas</option><option value="atrasado">Atrasadas</option>
      </select>
      <button class="btn bp" onclick="gFat()">🔄 Gerar Mês</button>
    </div>
  </div>
  <div class="g3" style="margin-bottom:12px" id="fst"></div>
  <div class="card"><div class="tw">
    <table><thead><tr><th>Cliente</th><th>Plano</th><th>Valor</th><th>Vencimento</th><th>Status</th><th>Ações</th></tr></thead>
    <tbody id="tft"></tbody></table>
    <div id="eft" class="empty" style="display:none"><div class="ei">💰</div>Nenhuma fatura.</div>
  </div></div>
</div>

<div id="page-portal" class="page">
  <div class="pcw"><div class="pcc">
    <div class="pch"><div style="font-size:36px">📡</div><h2 id="pct">Minha Conta</h2><p>Plano, faturas e rede Wi-Fi</p></div>
    <div id="pcb"></div>
  </div></div>
</div>

</main>
</div>

<!-- MODAIS -->
<div class="mo" id="m-cli">
  <div class="md">
    <div class="mh"><div class="mt" id="mct">Novo Cliente</div><button class="mc" onclick="cM('m-cli')">✕</button></div>
    <input type="hidden" id="eci">
    <div class="sec">Dados Pessoais</div>
    <div class="g2"><div class="fg"><label>Nome *</label><input id="cn" placeholder="João Silva"></div>
    <div class="fg"><label>CPF / CNPJ *</label><input id="cc" placeholder="000.000.000-00"></div></div>
    <div class="g2"><div class="fg"><label>Telefone</label><input id="ct2" placeholder="(00) 00000-0000"></div>
    <div class="fg"><label>E-mail</label><input id="ce" placeholder="email@exemplo.com"></div></div>
    <div class="fg"><label>Endereço</label><input id="cen" placeholder="Rua, número, bairro, cidade"></div>
    <div class="sec">Plano e Contrato</div>
    <div class="g2"><div class="fg"><label>Plano *</label><select id="cpl"></select></div>
    <div class="fg"><label>Vencimento *</label>
      <select id="cvn"><option value="5">Dia 5</option><option value="10">Dia 10</option><option value="15">Dia 15</option><option value="20">Dia 20</option><option value="25">Dia 25</option></select>
    </div></div>
    <div class="fg"><label>Status</label>
      <select id="cst"><option value="ativo">Ativo</option><option value="inativo">Inativo</option><option value="suspenso">Suspenso</option></select>
    </div>
    <div class="fg"><label>Observações</label><textarea id="cob" rows="2" style="resize:vertical"></textarea></div>
    <div class="mft"><button class="btn bg2" onclick="cM('m-cli')">Cancelar</button><button class="btn bp" onclick="sCli()">💾 Salvar</button></div>
  </div>
</div>

<div class="mo" id="m-eq">
  <div class="md">
    <div class="mh"><div class="mt" id="met">Novo Equipamento</div><button class="mc" onclick="cM('m-eq')">✕</button></div>
    <input type="hidden" id="eei">
    <div class="sec">Cliente</div>
    <div class="fg"><label>Cliente *</label><select id="eqc"></select></div>
    <div class="sec">Equipamento</div>
    <div class="g2"><div class="fg"><label>Modelo *</label><input id="eqm" placeholder="TP-Link, Mikrotik…"></div>
    <div class="fg"><label>Série / MAC</label><input id="eqs" placeholder="AA:BB:CC:DD:EE:FF"></div></div>
    <div class="g2"><div class="fg"><label>IP do Roteador *</label><input id="eqi" placeholder="192.168.0.1"></div>
    <div class="fg"><label>Tipo</label>
      <select id="eqt"><option>Roteador</option><option>ONU/ONT</option><option>CPE Rádio</option><option>Switch</option><option>Outro</option></select>
    </div></div>
    <div class="sec">Acesso ao Painel</div>
    <div class="g2"><div class="fg"><label>Usuário painel</label><input id="equ" placeholder="admin"></div>
    <div class="fg"><label>Senha painel</label><input id="eqp" type="password" placeholder="admin123"></div></div>
    <div class="sec">Wi-Fi</div>
    <div class="g2"><div class="fg"><label>SSID (nome da rede)</label><input id="eqss" placeholder="RadioNet-Cliente"></div>
    <div class="fg"><label>Senha Wi-Fi</label><input id="eqsw" placeholder="senha do cliente"></div></div>
    <div class="fg"><label>Observações</label><textarea id="eqob" rows="2" style="resize:vertical"></textarea></div>
    <div class="mft"><button class="btn bg2" onclick="cM('m-eq')">Cancelar</button><button class="btn bp" onclick="sEq()">💾 Salvar</button></div>
  </div>
</div>

<div class="mo" id="m-ts">
  <div class="md" style="max-width:400px">
    <div class="mh"><div class="mt">🔑 Alterar Senha Wi-Fi</div><button class="mc" onclick="cM('m-ts')">✕</button></div>
    <input type="hidden" id="tsi">
    <div id="tsinfo" style="background:var(--sf2);border-radius:8px;padding:10px;margin-bottom:12px;font-size:12px;color:var(--mu)"></div>
    <div class="fg"><label>Nome da rede (SSID)</label><input id="tssd"></div>
    <div class="fg"><label>Nova senha *</label><input id="ts1" type="password" placeholder="Mínimo 8 caracteres"></div>
    <div class="fg"><label>Confirmar *</label><input id="ts2" type="password" placeholder="Repita a senha"></div>
    <div class="mft"><button class="btn bg2" onclick="cM('m-ts')">Cancelar</button><button class="btn bp" onclick="cTS()">✅ Salvar</button></div>
  </div>
</div>

<div class="mo" id="m-pl">
  <div class="md">
    <div class="mh"><div class="mt" id="mpt">Novo Plano</div><button class="mc" onclick="cM('m-pl')">✕</button></div>
    <input type="hidden" id="epi">
    <div class="g2"><div class="fg"><label>Nome *</label><input id="pn" placeholder="Básico 50MB"></div>
    <div class="fg"><label>Velocidade (Mbps) *</label><input id="pmb" type="number" placeholder="100" min="1"></div></div>
    <div class="g2"><div class="fg"><label>Preço (R$) *</label><input id="ppr" type="number" placeholder="79.90" step="0.01"></div>
    <div class="fg"><label>Tipo</label><select id="ptp"><option>Fibra</option><option>Rádio</option><option>Misto</option></select></div></div>
    <div class="fg"><label>Descrição</label><textarea id="pds" rows="2" style="resize:vertical"></textarea></div>
    <div class="mft"><button class="btn bg2" onclick="cM('m-pl')">Cancelar</button><button class="btn bp" onclick="sPl()">💾 Salvar</button></div>
  </div>
</div>

<div class="mo" id="m-rd">
  <div class="md" style="max-width:440px">
    <div class="mh"><div class="mt">Nova Rede Wi-Fi</div><button class="mc" onclick="cM('m-rd')">✕</button></div>
    <input type="hidden" id="eri">
    <div class="fg"><label>Ponto de acesso</label><input id="rloc" placeholder="Torre Centro…"></div>
    <div class="g2"><div class="fg"><label>SSID *</label><input id="rss" placeholder="RadioNet-Fibra"></div>
    <div class="fg"><label>Senha *</label><input id="rsn" placeholder="senha123"></div></div>
    <div class="g2"><div class="fg"><label>Frequência</label><select id="rfq"><option>2.4 GHz</option><option>5 GHz</option><option>Dual Band</option></select></div>
    <div class="fg"><label>Status</label><select id="rst"><option value="online">Online</option><option value="offline">Offline</option><option value="manutencao">Manutenção</option></select></div></div>
    <div class="mft"><button class="btn bg2" onclick="cM('m-rd')">Cancelar</button><button class="btn bp" onclick="sRd()">💾 Salvar</button></div>
  </div>
</div>

<div class="mo" id="m-fc">
  <div class="md" style="max-width:560px">
    <div class="mh"><div class="mt" id="fct">Faturas</div><button class="mc" onclick="cM('m-fc')">✕</button></div>
    <div id="fcb"></div>
  </div>
</div>

<div id="toast"></div>

<script>
var DB = {
  g: function(k) { try { return JSON.parse(localStorage.getItem('rn_' + k) || '[]'); } catch(e) { return []; } },
  s: function(k, v) { localStorage.setItem('rn_' + k, JSON.stringify(v)); },
  id: function(k) { var d = DB.g(k); return d.length ? Math.max.apply(null, d.map(function(x) { return x.id; })) + 1 : 1; }
};

// Seed inicial
(function() {
  if (!DB.g('planos').length) {
    DB.s('planos', [
      {id:1,nome:'Básico 50MB',mb:50,preco:59.90,tipo:'Rádio',desc:'Uso básico'},
      {id:2,nome:'Standard 100MB',mb:100,preco:89.90,tipo:'Rádio',desc:'Famílias'},
      {id:3,nome:'Plus 300MB',mb:300,preco:129.90,tipo:'Fibra',desc:'Alta performance'},
      {id:4,nome:'Ultra 500MB',mb:500,preco:179.90,tipo:'Fibra',desc:'Empresas'}
    ]);
  }
  if (!DB.g('redes').length) {
    DB.s('redes', [
      {id:1,local:'Torre Central',ssid:'RadioNet-Principal',senha:'radionet2024',freq:'Dual Band',status:'online'},
      {id:2,local:'Antena Norte',ssid:'RadioNet-Norte',senha:'rn@norte24',freq:'5 GHz',status:'online'}
    ]);
  }
})();

var S = null;
var USERS = [{user:'Nicolas',pass:'2010',nome:'Nicolas',role:'CEO'}];

function setTab(n) {
  document.getElementById('t0').className = n === 0 ? 'on' : '';
  document.getElementById('t1').className = n === 1 ? 'on' : '';
  document.getElementById('fa').style.display = n === 0 ? '' : 'none';
  document.getElementById('fc').style.display = n === 1 ? '' : 'none';
  var e = document.getElementById('lerr');
  e.style.display = 'none';
}

function showErr(m) {
  var e = document.getElementById('lerr');
  e.textContent = m;
  e.style.display = 'block';
  setTimeout(function() { e.style.display = 'none'; }, 3500);
}

function soNums(s) { return s.replace(/[^0-9]/g, ''); }

function lAdm() {
  var u = document.getElementById('au').value.trim();
  var p = document.getElementById('ap').value;
  var f = null;
  for (var i = 0; i < USERS.length; i++) {
    if (USERS[i].user.toLowerCase() === u.toLowerCase() && USERS[i].pass === p) { f = USERS[i]; break; }
  }
  if (!f) { showErr('Usuário ou senha incorretos.'); return; }
  S = {tipo: 'admin', nome: f.nome, role: f.role, cid: null};
  entrar();
}

function lCli() {
  var cpf = document.getElementById('cu').value.trim();
  var pw = document.getElementById('cp').value.trim();
  if (!cpf || !pw) { showErr('Preencha CPF e senha.'); return; }
  var cls = DB.g('clientes');
  var cl = null;
  var n = soNums(cpf);
  for (var i = 0; i < cls.length; i++) {
    if (soNums(cls[i].cpf) === n) { cl = cls[i]; break; }
  }
  if (!cl) { showErr('CPF não encontrado.'); return; }
  var esp = soNums(cl.cpf).slice(-4);
  if (pw !== esp) { showErr('Senha incorreta. Use os últimos 4 dígitos do CPF.'); return; }
  S = {tipo: 'cliente', nome: cl.nome.split(' ')[0], role: 'Cliente', cid: cl.id};
  entrar();
}

function entrar() {
  document.getElementById('ls').style.display = 'none';
  document.getElementById('main-header').style.display = '';
  document.getElementById('main-app').style.display = 'flex';
  document.getElementById('hnm').textContent = S.nome;
  document.getElementById('hrl').textContent = S.role;
  if (S.tipo === 'admin') {
    document.getElementById('hs').style.display = 'flex';
    var nbs = document.getElementById('nav').querySelectorAll('.nb');
    for (var i = 0; i < nbs.length; i++) nbs[i].style.display = '';
    go('dashboard', document.querySelector('.nb[data-p="dashboard"]'));
  } else {
    document.getElementById('hs').style.display = 'none';
    var nbs2 = document.getElementById('nav').querySelectorAll('.nb');
    for (var i = 0; i < nbs2.length; i++) nbs2[i].style.display = 'none';
    var nav = document.getElementById('nav');
    if (!nav.querySelector('[data-p="portal"]')) {
      var l = document.createElement('div'); l.className = 'nl'; l.textContent = 'Minha Conta'; nav.appendChild(l);
      var btn = document.createElement('button');
      btn.className = 'nb on'; btn.setAttribute('data-p', 'portal');
      btn.innerHTML = '<span class="ic">🔑</span>Minha Conta';
      btn.setAttribute('onclick', 'go("portal",this)');
      nav.appendChild(btn);
    }
    go('portal', nav.querySelector('[data-p="portal"]'));
    rPortal();
  }
}

function sair() {
  if (!confirm('Deseja sair?')) return;
  S = null;
  document.getElementById('au').value = '';
  document.getElementById('ap').value = '';
  document.getElementById('cu').value = '';
  document.getElementById('cp').value = '';
  document.getElementById('ls').style.display = 'flex';
}

function go(id, btn) {
  var pages = document.querySelectorAll('.page');
  for (var i = 0; i < pages.length; i++) pages[i].className = 'page';
  var nbs = document.querySelectorAll('.nb');
  for (var i = 0; i < nbs.length; i++) nbs[i].className = 'nb';
  var pg = document.getElementById('page-' + id);
  if (pg) pg.className = 'page on';
  if (btn) btn.className = 'nb on';
  if (id === 'dashboard') rDash();
  else if (id === 'clientes') rCli();
  else if (id === 'equipamentos') rEq();
  else if (id === 'planos') rPl();
  else if (id === 'redes') rRd();
  else if (id === 'faturas') rFat();
  else if (id === 'portal') rPortal();
}

function oM(id) { document.getElementById(id).className = 'mo on'; }
function cM(id) { document.getElementById(id).className = 'mo'; }

function toast(m, t) {
  var el = document.getElementById('toast');
  el.textContent = (t === 'er' ? '❌ ' : '✅ ') + m;
  el.className = 'on ' + (t === 'er' ? 'er' : 'ok');
  setTimeout(function() { el.className = ''; }, 3000);
}

function fd(s) {
  if (!s) return '—';
  var p = s.split('-');
  return p[2] + '/' + p[1] + '/' + p[0];
}

function uHdr() {
  var cl = DB.g('clientes'), pl = DB.g('planos');
  var at = 0, rc = 0;
  for (var i = 0; i < cl.length; i++) {
    if (cl[i].status === 'ativo') {
      at++;
      for (var j = 0; j < pl.length; j++) { if (pl[j].id === cl[i].planoId) { rc += pl[j].preco; break; } }
    }
  }
  document.getElementById('h1').textContent = cl.length;
  document.getElementById('h2').textContent = at;
  document.getElementById('h3').textContent = 'R$' + rc.toFixed(0);
}

function bc(st) { return st === 'ativo' ? 'bgn2' : st === 'suspenso' ? 'byw' : 'brd'; }

// Toggle senha seguro via event delegation
document.addEventListener('click', function(e) {
  var el = e.target;
  while (el && !el.classList.contains('spw')) el = el.parentElement;
  if (!el) return;
  var sp = el.querySelector('[data-pw]');
  var tl = el.querySelector('.tl');
  var pw = el.getAttribute('data-s') || '';
  if (!sp) return;
  if (sp.textContent === '••••••••') { sp.textContent = pw; if (tl) tl.textContent = 'ocultar'; }
  else { sp.textContent = '••••••••'; if (tl) tl.textContent = 'mostrar'; }
});

// ── DASHBOARD ──
function rDash() {
  uHdr();
  var cl = DB.g('clientes'), pl = DB.g('planos'), ft = DB.g('faturas');
  var at = 0, rc = 0;
  for (var i = 0; i < cl.length; i++) {
    if (cl[i].status === 'ativo') {
      at++;
      for (var j = 0; j < pl.length; j++) { if (pl[j].id === cl[i].planoId) { rc += pl[j].preco; break; } }
    }
  }
  var pd = 0;
  for (var i = 0; i < ft.length; i++) { if (ft[i].status === 'pendente' || ft[i].status === 'atrasado') pd++; }
  document.getElementById('ds').innerHTML =
    '<div class="sc"><div class="sl">Total Clientes</div><div class="sv bl">' + cl.length + '</div></div>' +
    '<div class="sc"><div class="sl">Ativos</div><div class="sv gn">' + at + '</div></div>' +
    '<div class="sc"><div class="sl">Receita Mensal</div><div class="sv bl">R$' + rc.toFixed(0) + '</div></div>' +
    '<div class="sc"><div class="sl">Fat. Pendentes</div><div class="sv yw">' + pd + '</div></div>';
  var h = '';
  for (var i = cl.length - 1; i >= Math.max(0, cl.length - 5); i--) {
    var c = cl[i], pn = '—';
    for (var j = 0; j < pl.length; j++) { if (pl[j].id === c.planoId) { pn = pl[j].nome; break; } }
    h += '<div class="fi"><div><h4>' + c.nome + '</h4><p>' + pn + ' · ' + (c.telefone || 'S/tel') + '</p></div><span class="bx ' + bc(c.status) + '">' + c.status + '</span></div>';
  }
  document.getElementById('dcl').innerHTML = h || '<div class="empty"><div class="ei">👥</div>Sem clientes</div>';
  var pr = [], h2 = '';
  for (var i = 0; i < ft.length; i++) { if (ft[i].status === 'pendente') pr.push(ft[i]); }
  pr.sort(function(a, b) { return new Date(a.venc) - new Date(b.venc); });
  for (var i = 0; i < Math.min(5, pr.length); i++) {
    var c2 = null;
    for (var j = 0; j < cl.length; j++) { if (cl[j].id === pr[i].clienteId) { c2 = cl[j]; break; } }
    h2 += '<div class="fi"><div><h4>' + (c2 ? c2.nome : '—') + '</h4><p>Vence: ' + fd(pr[i].venc) + '</p></div><div class="fv">R$' + pr[i].valor.toFixed(2).replace('.', ',') + '</div></div>';
  }
  document.getElementById('dft').innerHTML = h2 || '<div class="empty"><div class="ei">💰</div>Nenhuma pendente</div>';
}

// ── CLIENTES ──
function rCli() {
  uHdr();
  var pl = DB.g('planos');
  var q = (document.getElementById('sc').value || '').toLowerCase();
  var cl = DB.g('clientes');
  if (q) { var tmp = []; for (var i = 0; i < cl.length; i++) { if (cl[i].nome.toLowerCase().indexOf(q) >= 0 || cl[i].cpf.indexOf(q) >= 0) tmp.push(cl[i]); } cl = tmp; }
  var tb = document.getElementById('tcl'), em = document.getElementById('ecl');
  if (!cl.length) { tb.innerHTML = ''; em.style.display = ''; return; }
  em.style.display = 'none';
  var h = '';
  for (var i = 0; i < cl.length; i++) {
    var c = cl[i], pn = '—', pmb = '';
    for (var j = 0; j < pl.length; j++) { if (pl[j].id === c.planoId) { pn = pl[j].nome; pmb = pl[j].mb + 'MB'; break; } }
    h += '<tr><td><b>' + c.nome + '</b></td>' +
      '<td style="font-family:\'DM Mono\',monospace;font-size:11px">' + c.cpf + '</td>' +
      '<td>' + (c.telefone || '—') + '</td>' +
      '<td>' + (pmb ? '<span class="pt2">⚡' + pmb + '</span>' : '—') + '</td>' +
      '<td style="font-family:\'DM Mono\',monospace">Dia ' + c.venc + '</td>' +
      '<td><span class="bx ' + bc(c.status) + '">' + c.status + '</span></td>' +
      '<td><div class="fx"><button class="btn bs bg2" onclick="vFC(' + c.id + ')">💳</button>' +
      '<button class="btn bs bg2" onclick="eCli(' + c.id + ')">✏️</button>' +
      '<button class="btn bs br" onclick="dCli(' + c.id + ')">🗑</button></div></td></tr>';
  }
  tb.innerHTML = h;
}

function oCli() {
  document.getElementById('eci').value = '';
  document.getElementById('mct').textContent = 'Novo Cliente';
  var ids = ['cn','cc','ct2','ce','cen','cob'];
  for (var i = 0; i < ids.length; i++) document.getElementById(ids[i]).value = '';
  document.getElementById('cst').value = 'ativo';
  document.getElementById('cvn').value = '10';
  var pl = DB.g('planos'), h = '';
  for (var i = 0; i < pl.length; i++) h += '<option value="' + pl[i].id + '">' + pl[i].nome + ' — R$' + pl[i].preco.toFixed(2) + '</option>';
  document.getElementById('cpl').innerHTML = h;
  oM('m-cli');
}

function eCli(id) {
  var cl = DB.g('clientes'), c = null;
  for (var i = 0; i < cl.length; i++) { if (cl[i].id === id) { c = cl[i]; break; } }
  if (!c) return;
  document.getElementById('eci').value = id;
  document.getElementById('mct').textContent = 'Editar Cliente';
  document.getElementById('cn').value = c.nome;
  document.getElementById('cc').value = c.cpf;
  document.getElementById('ct2').value = c.telefone || '';
  document.getElementById('ce').value = c.email || '';
  document.getElementById('cen').value = c.endereco || '';
  document.getElementById('cob').value = c.obs || '';
  document.getElementById('cst').value = c.status;
  document.getElementById('cvn').value = c.venc;
  var pl = DB.g('planos'), h = '';
  for (var i = 0; i < pl.length; i++) h += '<option value="' + pl[i].id + '"' + (pl[i].id === c.planoId ? ' selected' : '') + '>' + pl[i].nome + ' — R$' + pl[i].preco.toFixed(2) + '</option>';
  document.getElementById('cpl').innerHTML = h;
  oM('m-cli');
}

function sCli() {
  var nm = document.getElementById('cn').value.trim();
  var cpf = document.getElementById('cc').value.trim();
  var pid = parseInt(document.getElementById('cpl').value);
  if (!nm || !cpf || !pid) { toast('Preencha nome, CPF e plano', 'er'); return; }
  var d = {nome:nm,cpf:cpf,telefone:document.getElementById('ct2').value.trim(),email:document.getElementById('ce').value.trim(),endereco:document.getElementById('cen').value.trim(),planoId:pid,venc:parseInt(document.getElementById('cvn').value),status:document.getElementById('cst').value,obs:document.getElementById('cob').value.trim()};
  var eid = document.getElementById('eci').value;
  var cl = DB.g('clientes');
  if (eid) {
    for (var i = 0; i < cl.length; i++) { if (cl[i].id === parseInt(eid)) { for (var k in d) cl[i][k] = d[k]; break; } }
    toast('Cliente atualizado!');
  } else {
    d.id = DB.id('clientes'); cl.push(d); toast('Cliente cadastrado!');
  }
  DB.s('clientes', cl); cM('m-cli'); rCli(); uHdr();
}

function dCli(id) {
  if (!confirm('Deletar cliente?')) return;
  var cl = DB.g('clientes'), ft = DB.g('faturas'), eq = DB.g('equipamentos');
  DB.s('clientes', cl.filter(function(c) { return c.id !== id; }));
  DB.s('faturas', ft.filter(function(f) { return f.clienteId !== id; }));
  DB.s('equipamentos', eq.filter(function(e) { return e.clienteId !== id; }));
  toast('Removido.'); rCli(); uHdr();
}

function vFC(cid) {
  var cl = DB.g('clientes'), pl = DB.g('planos'), ft = DB.g('faturas');
  var c = null;
  for (var i = 0; i < cl.length; i++) { if (cl[i].id === cid) { c = cl[i]; break; } }
  document.getElementById('fct').textContent = 'Faturas — ' + (c ? c.nome : '');
  var list = [];
  for (var i = 0; i < ft.length; i++) { if (ft[i].clienteId === cid) list.push(ft[i]); }
  list.sort(function(a, b) { return new Date(b.venc) - new Date(a.venc); });
  var sm = {pago:'bgn2',pendente:'byw',atrasado:'brd'};
  var h = '';
  for (var i = 0; i < list.length; i++) {
    var f = list[i], pn = '—';
    for (var j = 0; j < pl.length; j++) { if (pl[j].id === f.planoId) { pn = pl[j].nome; break; } }
    h += '<div class="fi"><div><h4>' + pn + '</h4><p>Venc: ' + fd(f.venc) + (f.pagoEm ? ' · Pago: ' + fd(f.pagoEm) : '') + '</p></div>' +
      '<div class="fx"><div class="fv">R$' + f.valor.toFixed(2).replace('.', ',') + '</div><span class="bx ' + (sm[f.status] || 'bbl') + '">' + f.status + '</span>' +
      (f.status !== 'pago' ? '<button class="btn bs bgn" onclick="pFat(' + f.id + ');vFC(' + cid + ')">✓</button>' : '') + '</div></div>';
  }
  document.getElementById('fcb').innerHTML = h || '<div class="empty"><div class="ei">💰</div>Sem faturas</div>';
  oM('m-fc');
}

// ── EQUIPAMENTOS ──
function rEq() {
  var q = (document.getElementById('se').value || '').toLowerCase();
  var eqs = DB.g('equipamentos'), cls = DB.g('clientes');
  if (q) {
    var tmp = [];
    for (var i = 0; i < eqs.length; i++) {
      var e = eqs[i], cl = null;
      for (var j = 0; j < cls.length; j++) { if (cls[j].id === e.clienteId) { cl = cls[j]; break; } }
      if ((cl && cl.nome.toLowerCase().indexOf(q) >= 0) || (e.ip && e.ip.indexOf(q) >= 0) || (e.modelo && e.modelo.toLowerCase().indexOf(q) >= 0)) tmp.push(e);
    }
    eqs = tmp;
  }
  var el = document.getElementById('leq');
  if (!eqs.length) { el.innerHTML = '<div class="empty"><div class="ei">🖥️</div>Nenhum equipamento.</div>'; return; }
  var h = '';
  for (var i = 0; i < eqs.length; i++) {
    var e = eqs[i], cl = null;
    for (var j = 0; j < cls.length; j++) { if (cls[j].id === e.clienteId) { cl = cls[j]; break; } }
    h += '<div class="ec">' +
      '<div style="display:flex;justify-content:space-between;align-items:start;flex-wrap:wrap;gap:7px">' +
        '<div>' +
          '<div style="font-size:11px;color:var(--mu);margin-bottom:3px">' + (cl ? cl.nome : '?') + '</div>' +
          '<div style="font-family:\'Syne\',sans-serif;font-size:13px;font-weight:700">🖥️ ' + (e.modelo || '—') + '</div>' +
          '<div style="font-size:11px;color:var(--mu);margin-top:2px">📡 <span class="ipb">' + (e.ip || '—') + '</span> 🏷️ ' + (e.tipo || '—') + '</div>' +
        '</div>' +
        '<div class="fx">' +
          '<button class="btn bs bor" onclick="aTS(' + e.id + ')">🔑 Senha</button>' +
          '<button class="btn bs bg2" onclick="edEq(' + e.id + ')">✏️</button>' +
          '<button class="btn bs br" onclick="dEq(' + e.id + ')">🗑</button>' +
        '</div>' +
      '</div>';
    if (e.ssid) {
      var pw = e.senhaWifi || '';
      h += '<div style="margin-top:9px;padding-top:9px;border-top:1px solid var(--bd);font-size:12px;color:var(--mu);display:flex;align-items:center;gap:10px;flex-wrap:wrap">' +
        '📶 ' + e.ssid +
        ' <span class="spw" data-s="' + pw.replace(/&/g,'&amp;').replace(/"/g,'&quot;') + '">Senha: <span data-pw="1">••••••••</span> <span class="tl">mostrar</span></span>' +
      '</div>';
    }
    h += '</div>';
  }
  el.innerHTML = h;
}

function oEq() {
  var cls = DB.g('clientes');
  if (!cls.length) { toast('Cadastre um cliente primeiro', 'er'); return; }
  document.getElementById('eei').value = '';
  document.getElementById('met').textContent = 'Novo Equipamento';
  var ids = ['eqm','eqs','eqi','equ','eqp','eqss','eqsw','eqob'];
  for (var i = 0; i < ids.length; i++) document.getElementById(ids[i]).value = '';
  document.getElementById('eqt').value = 'Roteador';
  var h = '';
  for (var i = 0; i < cls.length; i++) h += '<option value="' + cls[i].id + '">' + cls[i].nome + ' — ' + cls[i].cpf + '</option>';
  document.getElementById('eqc').innerHTML = h;
  oM('m-eq');
}

function edEq(id) {
  var eqs = DB.g('equipamentos'), e = null;
  for (var i = 0; i < eqs.length; i++) { if (eqs[i].id === id) { e = eqs[i]; break; } }
  if (!e) return;
  var cls = DB.g('clientes');
  document.getElementById('eei').value = id;
  document.getElementById('met').textContent = 'Editar Equipamento';
  var h = '';
  for (var i = 0; i < cls.length; i++) h += '<option value="' + cls[i].id + '"' + (cls[i].id === e.clienteId ? ' selected' : '') + '>' + cls[i].nome + '</option>';
  document.getElementById('eqc').innerHTML = h;
  document.getElementById('eqm').value = e.modelo || '';
  document.getElementById('eqs').value = e.serial || '';
  document.getElementById('eqi').value = e.ip || '';
  document.getElementById('eqt').value = e.tipo || 'Roteador';
  document.getElementById('equ').value = e.userPainel || '';
  document.getElementById('eqp').value = e.passPainel || '';
  document.getElementById('eqss').value = e.ssid || '';
  document.getElementById('eqsw').value = e.senhaWifi || '';
  document.getElementById('eqob').value = e.obs || '';
  oM('m-eq');
}

function sEq() {
  var cid = parseInt(document.getElementById('eqc').value);
  var ip = document.getElementById('eqi').value.trim();
  var mod = document.getElementById('eqm').value.trim();
  if (!cid || !ip || !mod) { toast('Preencha cliente, modelo e IP', 'er'); return; }
  var d = {clienteId:cid,modelo:mod,serial:document.getElementById('eqs').value.trim(),ip:ip,tipo:document.getElementById('eqt').value,userPainel:document.getElementById('equ').value.trim(),passPainel:document.getElementById('eqp').value.trim(),ssid:document.getElementById('eqss').value.trim(),senhaWifi:document.getElementById('eqsw').value.trim(),obs:document.getElementById('eqob').value.trim()};
  var eid = document.getElementById('eei').value;
  var eqs = DB.g('equipamentos');
  if (eid) {
    for (var i = 0; i < eqs.length; i++) { if (eqs[i].id === parseInt(eid)) { for (var k in d) eqs[i][k] = d[k]; break; } }
    toast('Equipamento atualizado!');
  } else {
    d.id = DB.id('equipamentos'); eqs.push(d); toast('Equipamento cadastrado!');
  }
  DB.s('equipamentos', eqs); cM('m-eq'); rEq();
}

function dEq(id) {
  if (!confirm('Remover?')) return;
  DB.s('equipamentos', DB.g('equipamentos').filter(function(e) { return e.id !== id; }));
  toast('Removido.'); rEq();
}

function aTS(eid) {
  var eqs = DB.g('equipamentos'), e = null;
  for (var i = 0; i < eqs.length; i++) { if (eqs[i].id === eid) { e = eqs[i]; break; } }
  if (!e) return;
  var cls = DB.g('clientes'), cl = null;
  for (var i = 0; i < cls.length; i++) { if (cls[i].id === e.clienteId) { cl = cls[i]; break; } }
  document.getElementById('tsi').value = eid;
  document.getElementById('tssd').value = e.ssid || '';
  document.getElementById('ts1').value = '';
  document.getElementById('ts2').value = '';
  document.getElementById('tsinfo').textContent = (cl ? cl.nome : '—') + ' · ' + e.modelo + ' · ' + e.ip;
  oM('m-ts');
}

function cTS() {
  var id = parseInt(document.getElementById('tsi').value);
  var ssid = document.getElementById('tssd').value.trim();
  var s1 = document.getElementById('ts1').value;
  var s2 = document.getElementById('ts2').value;
  if (!s1) { toast('Digite a nova senha', 'er'); return; }
  if (s1.length < 8) { toast('Senha mínima 8 caracteres', 'er'); return; }
  if (s1 !== s2) { toast('Senhas não coincidem', 'er'); return; }
  var eqs = DB.g('equipamentos');
  for (var i = 0; i < eqs.length; i++) { if (eqs[i].id === id) { if (ssid) eqs[i].ssid = ssid; eqs[i].senhaWifi = s1; break; } }
  DB.s('equipamentos', eqs); toast('Senha alterada!'); cM('m-ts'); rEq();
}

// ── PLANOS ──
function rPl() {
  var pl = DB.g('planos'), cl = DB.g('clientes');
  var gd = document.getElementById('gpl');
  if (!pl.length) { gd.innerHTML = '<div class="empty"><div class="ei">⚡</div>Nenhum plano.</div>'; return; }
  var h = '';
  for (var i = 0; i < pl.length; i++) {
    var p = pl[i], cnt = 0;
    for (var j = 0; j < cl.length; j++) { if (cl[j].planoId === p.id && cl[j].status === 'ativo') cnt++; }
    h += '<div class="card">' +
      '<div style="display:flex;justify-content:space-between;align-items:start">' +
        '<div><div style="font-family:\'DM Mono\',monospace;font-size:28px;color:var(--ac)">' + p.mb + '<span style="font-size:13px">MB</span></div>' +
        '<div style="font-family:\'Syne\',sans-serif;font-size:14px;font-weight:700;margin:3px 0">' + p.nome + '</div>' +
        '<div style="font-size:11px;color:var(--mu)">' + p.tipo + ' · ' + (p.desc || '') + '</div></div>' +
        '<div><div style="font-family:\'DM Mono\',monospace;font-size:17px;color:var(--gn)">R$' + p.preco.toFixed(2).replace('.', ',') + '</div>' +
        '<div style="font-size:11px;color:var(--mu)">por mês</div></div>' +
      '</div>' +
      '<div class="dv"></div>' +
      '<div style="display:flex;justify-content:space-between;align-items:center">' +
        '<span style="font-size:11px;color:var(--mu)">' + cnt + ' ativo(s)</span>' +
        '<div class="fx"><button class="btn bs bg2" onclick="ePl(' + p.id + ')">✏️</button><button class="btn bs br" onclick="dPl(' + p.id + ')">🗑</button></div>' +
      '</div></div>';
  }
  gd.innerHTML = h;
}

function ePl(id) {
  var pl = DB.g('planos'), p = null;
  for (var i = 0; i < pl.length; i++) { if (pl[i].id === id) { p = pl[i]; break; } }
  if (!p) return;
  document.getElementById('epi').value = id;
  document.getElementById('mpt').textContent = 'Editar Plano';
  document.getElementById('pn').value = p.nome;
  document.getElementById('pmb').value = p.mb;
  document.getElementById('ppr').value = p.preco;
  document.getElementById('ptp').value = p.tipo;
  document.getElementById('pds').value = p.desc || '';
  oM('m-pl');
}

function sPl() {
  var nm = document.getElementById('pn').value.trim();
  var mb = parseInt(document.getElementById('pmb').value);
  var pr = parseFloat(document.getElementById('ppr').value);
  if (!nm || !mb || !pr) { toast('Preencha todos os campos', 'er'); return; }
  var d = {nome:nm,mb:mb,preco:pr,tipo:document.getElementById('ptp').value,desc:document.getElementById('pds').value.trim()};
  var eid = document.getElementById('epi').value;
  var pl = DB.g('planos');
  if (eid) {
    for (var i = 0; i < pl.length; i++) { if (pl[i].id === parseInt(eid)) { for (var k in d) pl[i][k] = d[k]; break; } }
    toast('Plano atualizado!');
  } else {
    d.id = DB.id('planos'); pl.push(d); toast('Plano criado!');
  }
  DB.s('planos', pl);
  document.getElementById('epi').value = ''; document.getElementById('mpt').textContent = 'Novo Plano';
  var ids = ['pn','pmb','ppr','pds'];
  for (var i = 0; i < ids.length; i++) document.getElementById(ids[i]).value = '';
  cM('m-pl'); rPl();
}

function dPl(id) {
  var cl = DB.g('clientes'), cnt = 0;
  for (var i = 0; i < cl.length; i++) { if (cl[i].planoId === id) cnt++; }
  if (cnt > 0 && !confirm('Plano tem ' + cnt + ' cliente(s). Deletar?')) return;
  DB.s('planos', DB.g('planos').filter(function(p) { return p.id !== id; }));
  toast('Plano removido.'); rPl();
}

// ── REDES ──
function rRd() {
  var rd = DB.g('redes');
  var el = document.getElementById('lrd');
  if (!rd.length) { el.innerHTML = '<div class="empty"><div class="ei">📶</div>Nenhuma rede.</div>'; return; }
  var sm = {online:'bgn2',offline:'brd',manutencao:'byw'};
  var sl = {online:'Online',offline:'Offline',manutencao:'Manutenção'};
  var h = '';
  for (var i = 0; i < rd.length; i++) {
    var r = rd[i];
    var pw = r.senha || '';
    h += '<div class="wc">' +
      '<div style="display:flex;justify-content:space-between;align-items:start;flex-wrap:wrap;gap:9px">' +
        '<div>' +
          '<div style="font-size:11px;color:var(--mu);margin-bottom:3px">' + (r.local || 'Ponto') + ' · ' + r.freq + '</div>' +
          '<div style="font-family:\'DM Mono\',monospace;font-size:16px;margin-bottom:4px">📶 ' + r.ssid + '</div>' +
          '<div class="spw" data-s="' + pw.replace(/&/g,'&amp;').replace(/"/g,'&quot;') + '">Senha: <span data-pw="1">••••••••</span> <span class="tl">mostrar</span></div>' +
        '</div>' +
        '<div class="fx"><span class="bx ' + (sm[r.status] || 'bbl') + '">' + (sl[r.status] || r.status) + '</span>' +
          '<button class="btn bs bg2" onclick="edRd(' + r.id + ')">✏️ Editar</button>' +
          '<button class="btn bs br" onclick="dRd(' + r.id + ')">🗑</button>' +
        '</div>' +
      '</div></div>';
  }
  el.innerHTML = h;
}

function edRd(id) {
  var rd = DB.g('redes'), r = null;
  for (var i = 0; i < rd.length; i++) { if (rd[i].id === id) { r = rd[i]; break; } }
  if (!r) return;
  document.getElementById('eri').value = id;
  document.getElementById('rloc').value = r.local || '';
  document.getElementById('rss').value = r.ssid;
  document.getElementById('rsn').value = r.senha;
  document.getElementById('rfq').value = r.freq;
  document.getElementById('rst').value = r.status;
  oM('m-rd');
}

function sRd() {
  var ssid = document.getElementById('rss').value.trim();
  var sn = document.getElementById('rsn').value.trim();
  if (!ssid || !sn) { toast('Preencha SSID e senha', 'er'); return; }
  var d = {local:document.getElementById('rloc').value.trim(),ssid:ssid,senha:sn,freq:document.getElementById('rfq').value,status:document.getElementById('rst').value};
  var eid = document.getElementById('eri').value;
  var rd = DB.g('redes');
  if (eid) {
    for (var i = 0; i < rd.length; i++) { if (rd[i].id === parseInt(eid)) { for (var k in d) rd[i][k] = d[k]; break; } }
    toast('Rede atualizada!');
  } else {
    d.id = DB.id('redes'); rd.push(d); toast('Rede cadastrada!');
  }
  DB.s('redes', rd);
  document.getElementById('eri').value = '';
  var ids = ['rloc','rss','rsn'];
  for (var i = 0; i < ids.length; i++) document.getElementById(ids[i]).value = '';
  cM('m-rd'); rRd();
}

function dRd(id) {
  if (!confirm('Remover rede?')) return;
  DB.s('redes', DB.g('redes').filter(function(r) { return r.id !== id; }));
  toast('Removida.'); rRd();
}

// ── FATURAS ──
function gFat() {
  var cl = DB.g('clientes'), pl = DB.g('planos'), ft = DB.g('faturas');
  var td = new Date(), g = 0;
  for (var i = 0; i < cl.length; i++) {
    var c = cl[i];
    if (c.status !== 'ativo') continue;
    var p = null;
    for (var j = 0; j < pl.length; j++) { if (pl[j].id === c.planoId) { p = pl[j]; break; } }
    if (!p) continue;
    var vd = new Date(td.getFullYear(), td.getMonth(), c.venc);
    var key = c.id + '-' + td.getFullYear() + '-' + (td.getMonth() + 1);
    var ex = false;
    for (var j = 0; j < ft.length; j++) { if (ft[j].chave === key) { ex = true; break; } }
    if (!ex) {
      ft.push({id:DB.id('faturas'),clienteId:c.id,planoId:c.planoId,valor:p.preco,venc:vd.toISOString().split('T')[0],status:td>vd?'atrasado':'pendente',chave:key});
      g++;
    }
  }
  DB.s('faturas', ft); toast(g + ' fatura(s) gerada(s)!'); rFat();
}

function rFat() {
  uHdr();
  var cl = DB.g('clientes'), pl = DB.g('planos');
  var ft = DB.g('faturas');
  var fil = document.getElementById('ffl').value;
  if (fil !== 'todos') { var tmp = []; for (var i = 0; i < ft.length; i++) { if (ft[i].status === fil) tmp.push(ft[i]); } ft = tmp; }
  ft.sort(function(a, b) { return new Date(a.venc) - new Date(b.venc); });
  var all = DB.g('faturas'), tv = 0, pv = 0, rv = 0;
  for (var i = 0; i < all.length; i++) { tv += all[i].valor; if (all[i].status === 'pago') pv += all[i].valor; else rv += all[i].valor; }
  document.getElementById('fst').innerHTML =
    '<div class="sc"><div class="sl">Total</div><div class="sv bl">R$' + tv.toFixed(0) + '</div></div>' +
    '<div class="sc"><div class="sl">Recebido</div><div class="sv gn">R$' + pv.toFixed(0) + '</div></div>' +
    '<div class="sc"><div class="sl">A Receber</div><div class="sv yw">R$' + rv.toFixed(0) + '</div></div>';
  var tb = document.getElementById('tft'), em = document.getElementById('eft');
  if (!ft.length) { tb.innerHTML = ''; em.style.display = ''; return; }
  em.style.display = 'none';
  var sm = {pago:'bgn2',pendente:'byw',atrasado:'brd'};
  var h = '';
  for (var i = 0; i < ft.length; i++) {
    var f = ft[i], cn = '—', pn = '—', pmb = '';
    for (var j = 0; j < cl.length; j++) { if (cl[j].id === f.clienteId) { cn = cl[j].nome; break; } }
    for (var j = 0; j < pl.length; j++) { if (pl[j].id === f.planoId) { pn = pl[j].nome; pmb = pl[j].mb + 'MB'; break; } }
    h += '<tr><td><b>' + cn + '</b></td>' +
      '<td><span class="pt2">⚡' + pmb + '</span></td>' +
      '<td style="font-family:\'DM Mono\',monospace">R$' + f.valor.toFixed(2).replace('.', ',') + '</td>' +
      '<td style="font-family:\'DM Mono\',monospace">' + fd(f.venc) + '</td>' +
      '<td><span class="bx ' + (sm[f.status] || 'bbl') + '">' + f.status + '</span></td>' +
      '<td><div class="fx">' +
        (f.status !== 'pago' ? '<button class="btn bs bgn" onclick="pFat(' + f.id + ')">✓ Pago</button>' : '<span style="font-size:11px;color:var(--mu)">Quitada</span>') +
        '<button class="btn bs br" onclick="dFat(' + f.id + ')">🗑</button>' +
      '</div></td></tr>';
  }
  tb.innerHTML = h;
}

function pFat(id) {
  var ft = DB.g('faturas');
  for (var i = 0; i < ft.length; i++) { if (ft[i].id === id) { ft[i].status = 'pago'; ft[i].pagoEm = new Date().toISOString().split('T')[0]; break; } }
  DB.s('faturas', ft); toast('Fatura paga!'); rFat();
}

function dFat(id) {
  if (!confirm('Remover fatura?')) return;
  DB.s('faturas', DB.g('faturas').filter(function(f) { return f.id !== id; }));
  toast('Removida.'); rFat();
}

// ── PORTAL CLIENTE ──
function rPortal() {
  if (!S || S.tipo !== 'cliente') return;
  var cls = DB.g('clientes'), pl = DB.g('planos'), eqs = DB.g('equipamentos'), fts = DB.g('faturas');
  var cl = null;
  for (var i = 0; i < cls.length; i++) { if (cls[i].id === S.cid) { cl = cls[i]; break; } }
  if (!cl) { document.getElementById('pcb').innerHTML = '<div class="empty"><div class="ei">⚠️</div>Erro ao carregar.</div>'; return; }
  var p = null;
  for (var i = 0; i < pl.length; i++) { if (pl[i].id === cl.planoId) { p = pl[i]; break; } }
  var myEqs = [], myFts = [];
  for (var i = 0; i < eqs.length; i++) { if (eqs[i].clienteId === S.cid) myEqs.push(eqs[i]); }
  for (var i = 0; i < fts.length; i++) { if (fts[i].clienteId === S.cid) myFts.push(fts[i]); }
  myFts.sort(function(a, b) { return new Date(a.venc) - new Date(b.venc); });
  document.getElementById('pct').textContent = 'Olá, ' + cl.nome.split(' ')[0] + '! 👋';
  var sc = cl.status === 'ativo' ? 'bgn2' : cl.status === 'suspenso' ? 'byw' : 'brd';
  var h = '<div class="pcinfo"><h3>📋 Meu Plano</h3>' +
    '<div class="ir"><span class="lb2">Status</span><span class="bx ' + sc + '">' + cl.status + '</span></div>' +
    '<div class="ir"><span class="lb2">Plano</span><span class="vl">' + (p ? p.nome : '—') + '</span></div>' +
    '<div class="ir"><span class="lb2">Velocidade</span><span class="vl">' + (p ? p.mb + ' Mbps' : '—') + '</span></div>' +
    '<div class="ir"><span class="lb2">Valor mensal</span><span class="vl">' + (p ? 'R$' + p.preco.toFixed(2).replace('.', ',') : '—') + '</span></div>' +
    '<div class="ir"><span class="lb2">Vencimento</span><span class="vl">Dia ' + cl.venc + '</span></div>' +
  '</div>';
  h += '<div style="margin-top:14px"><div class="ct">🖥️ Minha Rede Wi-Fi</div>';
  if (!myEqs.length) {
    h += '<div style="color:var(--mu);font-size:12px;text-align:center;padding:10px">Nenhum equipamento cadastrado.</div>';
  } else {
    for (var i = 0; i < myEqs.length; i++) {
      var e = myEqs[i];
      var pw = e.senhaWifi || '';
      h += '<div class="eqc">' +
        '<div style="font-weight:600;margin-bottom:9px;font-size:13px">🖥️ ' + e.modelo + ' <span class="ipb">' + e.ip + '</span></div>' +
        '<div class="ir"><span class="lb2">📶 Nome da rede</span><span class="vl">' + (e.ssid || '—') + '</span></div>' +
        '<div class="ir"><span class="lb2">🔑 Senha Wi-Fi</span>' +
          '<span class="spw" data-s="' + pw.replace(/&/g,'&amp;').replace(/"/g,'&quot;') + '"><span data-pw="1">••••••••</span> <span class="tl">mostrar</span></span>' +
        '</div>' +
        '<div style="margin-top:10px;padding-top:9px;border-top:1px solid var(--bd)">' +
          '<div style="font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.5px;color:var(--ac);margin-bottom:8px">✏️ Alterar Nome e Senha</div>' +
          '<div class="fg"><label>Novo nome da rede (SSID)</label><input id="pss' + e.id + '" value="' + (e.ssid || '').replace(/"/g, '&quot;') + '" placeholder="Nome da rede"></div>' +
          '<div class="g2"><div class="fg"><label>Nova senha</label><input id="ps1' + e.id + '" type="password" placeholder="Mín. 8 chars"></div>' +
          '<div class="fg"><label>Confirmar</label><input id="ps2' + e.id + '" type="password" placeholder="Repita"></div></div>' +
          '<button class="btn bp" style="width:100%;justify-content:center" onclick="sPCli(' + e.id + ')">💾 Salvar</button>' +
        '</div>' +
      '</div>';
    }
  }
  h += '</div><div style="margin-top:14px"><div class="ct">💳 Minhas Faturas</div>';
  var pend = [], pagas = [];
  for (var i = 0; i < myFts.length; i++) {
    if (myFts[i].status !== 'pago') pend.push(myFts[i]);
    else if (pagas.length < 3) pagas.push(myFts[i]);
  }
  if (!pend.length && !pagas.length) {
    h += '<div style="color:var(--mu);font-size:12px;text-align:center;padding:10px">Nenhuma fatura.</div>';
  } else {
    var smf = {pendente:'byw',atrasado:'brd'};
    if (pend.length) {
      for (var i = 0; i < pend.length; i++) {
        var f = pend[i], pn2 = '—';
        for (var j = 0; j < pl.length; j++) { if (pl[j].id === f.planoId) { pn2 = pl[j].nome; break; } }
        h += '<div class="fi"><div><h4>' + pn2 + '</h4><p>Vence: ' + fd(f.venc) + '</p></div>' +
          '<div class="fx"><div class="fv">R$' + f.valor.toFixed(2).replace('.', ',') + '</div><span class="bx ' + (smf[f.status] || 'byw') + '">' + f.status + '</span></div></div>';
      }
    } else {
      h += '<div style="background:rgba(0,230,118,.07);border:1px solid rgba(0,230,118,.16);border-radius:8px;padding:10px;text-align:center;color:var(--gn);font-size:12px">✅ Nenhuma fatura em aberto!</div>';
    }
    if (pagas.length) {
      h += '<div style="font-size:10px;color:var(--mu);text-transform:uppercase;margin:10px 0 6px">Pagas recentemente</div>';
      for (var i = 0; i < pagas.length; i++) {
        var f2 = pagas[i], pn3 = '—';
        for (var j = 0; j < pl.length; j++) { if (pl[j].id === f2.planoId) { pn3 = pl[j].nome; break; } }
        h += '<div class="fi"><div><h4>' + pn3 + '</h4><p>Pago: ' + fd(f2.pagoEm) + '</p></div><div class="fx"><div class="fv" style="font-size:14px">R$' + f2.valor.toFixed(2).replace('.', ',') + '</div><span class="bx bgn2">pago</span></div></div>';
      }
    }
  }
  h += '</div>';
  document.getElementById('pcb').innerHTML = h;
}

function sPCli(eid) {
  var ssEl = document.getElementById('pss' + eid);
  var s1El = document.getElementById('ps1' + eid);
  var s2El = document.getElementById('ps2' + eid);
  var ssid = ssEl ? ssEl.value.trim() : '';
  var s1 = s1El ? s1El.value : '';
  var s2 = s2El ? s2El.value : '';
  if (s1 && s1.length < 8) { toast('Senha mínima 8 caracteres', 'er'); return; }
  if (s1 && s1 !== s2) { toast('Senhas não coincidem', 'er'); return; }
  var eqs = DB.g('equipamentos');
  for (var i = 0; i < eqs.length; i++) {
    if (eqs[i].id === eid) {
      if (ssid) eqs[i].ssid = ssid;
      if (s1) eqs[i].senhaWifi = s1;
      break;
    }
  }
  DB.s('equipamentos', eqs); toast('Rede atualizada!'); rPortal();
}

// Fechar modal ao clicar fora
var mos = document.querySelectorAll('.mo');
for (var i = 0; i < mos.length; i++) {
  mos[i].addEventListener('click', function(e) { if (e.target === this) this.className = 'mo'; });
}
</script>
</body>
</html>

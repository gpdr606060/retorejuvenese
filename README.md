@import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;1,400&family=Work+Sans:wght@300;400;500&display=swap');

:root{
  --ivory:#F6F3EC;
  --white:#FCFBF7;
  --sage-deep:#3F4B3B;
  --sage:#8B9A82;
  --sage-pale:#D9E0D2;
  --gold:#A9824F;
  --charcoal:#2A2A24;
  --line: rgba(42,42,36,0.14);
  --maxw: 1120px;
}

*{box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{
  margin:0;
  background:var(--ivory);
  color:var(--charcoal);
  font-family:'Work Sans', sans-serif;
  font-weight:300;
  font-size:16px;
  line-height:1.6;
}
h1,h2,h3,.display{
  font-family:'Cormorant Garamond', serif;
  font-weight:500;
  color:var(--sage-deep);
  margin:0;
  letter-spacing:0.01em;
}
a{color:inherit; text-decoration:none;}
img,svg{display:block; max-width:100%;}

.wrap{max-width:var(--maxw); margin:0 auto; padding:0 32px;}

/* NAV */
header.site-nav{
  background:var(--sage-deep);
  color:var(--white);
}
.nav-inner{
  max-width:var(--maxw);
  margin:0 auto;
  padding:22px 32px;
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:24px;
  flex-wrap:wrap;
}
.nav-inner .brand{
  font-family:'Cormorant Garamond', serif;
  font-size:1.5rem;
  color:var(--white);
  font-weight:500;
  letter-spacing:0.02em;
}
.nav-inner .brand em{font-style:italic; color:var(--sage-pale);}
nav.links{display:flex; gap:30px;}
nav.links a{
  font-size:0.92rem;
  color:var(--sage-pale);
  padding-bottom:4px;
  border-bottom:1px solid transparent;
  transition:color .2s ease, border-color .2s ease;
}
nav.links a:hover, nav.links a.active{
  color:var(--white);
  border-bottom-color:var(--gold);
}

/* HERO */
.hero{
  padding:96px 32px 80px;
  max-width:var(--maxw);
  margin:0 auto;
  display:grid;
  grid-template-columns:1.2fr 0.8fr;
  gap:60px;
  align-items:center;
}
.hero h1{
  font-size:clamp(2.6rem, 5vw, 3.6rem);
  line-height:1.08;
}
.hero .lede{
  margin-top:22px;
  max-width:46ch;
  font-size:1.08rem;
  color:#4A4A40;
}
.hero-figure{position:relative;}
.cta-row{margin-top:36px; display:flex; gap:18px; flex-wrap:wrap; align-items:center;}
.btn{
  display:inline-block;
  padding:14px 30px;
  font-family:'Work Sans', sans-serif;
  font-size:0.94rem;
  border:1px solid var(--sage-deep);
  color:var(--sage-deep);
  transition:background .2s ease, color .2s ease;
}
.btn.primary{
  background:var(--sage-deep);
  color:var(--white);
}
.btn.primary:hover{background:var(--gold); border-color:var(--gold);}
.btn.ghost:hover{background:var(--sage-deep); color:var(--white);}
.link-gold{
  color:var(--gold);
  border-bottom:1px solid var(--gold);
  padding-bottom:2px;
  font-size:0.94rem;
}

hr.rule{
  border:none;
  border-top:1px solid var(--line);
  max-width:var(--maxw);
  margin:0 auto;
}
hr.rule.gold{border-top:2px solid var(--gold); width:64px; margin:0 0 26px;}

section{padding:76px 32px;}
section.tight{padding:50px 32px;}
.eyebrow{
  font-size:0.8rem;
  color:var(--sage);
  margin-bottom:10px;
}
.section-head{max-width:60ch; margin-bottom:44px;}
.section-head h2{font-size:clamp(2rem, 3.4vw, 2.6rem);}
.section-head p{margin-top:14px; color:#4A4A40;}

/* SERVICES LIST (no cards) */
.service-list{max-width:var(--maxw); margin:0 auto;}
.service-row{
  display:grid;
  grid-template-columns:1fr 2.2fr;
  gap:40px;
  padding:34px 0;
  border-top:1px solid var(--line);
}
.service-row:last-child{border-bottom:1px solid var(--line);}
.service-row h3{font-size:1.5rem; font-weight:500;}
.service-row .tag{font-size:0.78rem; color:var(--sage); margin-top:6px;}
.service-row p{color:#4A4A40; margin:0;}
.service-row ul{margin:14px 0 0; padding-left:18px; color:#4A4A40;}
.service-row li{margin-bottom:4px;}

/* LOCATIONS */
.locations-grid{
  max-width:var(--maxw); margin:0 auto;
  display:grid;
  grid-template-columns:repeat(2, 1fr);
  gap:1px;
  background:var(--line);
  border:1px solid var(--line);
}
.location-card{
  background:var(--white);
  padding:34px;
}
.location-card h3{font-size:1.4rem; margin-bottom:4px;}
.location-card .region{font-size:0.8rem; color:var(--sage); margin-bottom:14px;}
.location-card p{margin:0 0 6px; color:#4A4A40; font-size:0.95rem;}
.location-card a.link-gold{margin-top:12px; display:inline-block;}

/* ABOUT / VALUES */
.values-grid{
  max-width:var(--maxw); margin:0 auto;
  display:grid;
  grid-template-columns:repeat(3, 1fr);
  gap:44px;
}
.value-item h3{font-size:1.3rem; margin-bottom:10px;}
.value-item p{color:#4A4A40; font-size:0.96rem; margin:0;}

.split{
  max-width:var(--maxw); margin:0 auto;
  display:grid;
  grid-template-columns:0.9fr 1.1fr;
  gap:60px;
  align-items:start;
}

/* CONTACT FORM */
.contact-form{max-width:640px; margin:0 auto;}
.field{margin-bottom:22px;}
.field label{display:block; font-size:0.85rem; color:var(--sage-deep); margin-bottom:8px;}
.field input, .field textarea, .field select{
  width:100%;
  padding:12px 14px;
  border:1px solid var(--line);
  background:var(--white);
  font-family:'Work Sans', sans-serif;
  font-size:0.98rem;
  color:var(--charcoal);
}
.field input:focus, .field textarea:focus, .field select:focus{
  outline:2px solid var(--gold);
  outline-offset:1px;
}
.field-row{display:grid; grid-template-columns:1fr 1fr; gap:20px;}

/* FOOTER */
footer{
  background:var(--sage-deep);
  color:var(--sage-pale);
  padding:56px 32px 32px;
}
.footer-inner{
  max-width:var(--maxw); margin:0 auto;
  display:grid;
  grid-template-columns:1.4fr 1fr 1fr;
  gap:40px;
}
footer h4{color:var(--white); font-family:'Cormorant Garamond', serif; font-size:1.2rem; font-weight:500; margin:0 0 14px;}
footer p, footer a{font-size:0.9rem; color:var(--sage-pale);}
footer a:hover{color:var(--gold);}
.footer-bottom{
  max-width:var(--maxw); margin:36px auto 0;
  border-top:1px solid rgba(255,255,255,0.15);
  padding-top:20px;
  font-size:0.78rem;
  color:rgba(217,224,210,0.7);
}
.footer-bottom .disclaimer{max-width:80ch; margin-bottom:10px; line-height:1.6;}

/* leaf motif */
.leaf-motif{color:var(--sage);}

@media (max-width: 860px){
  .hero{grid-template-columns:1fr; padding-top:64px;}
  .split{grid-template-columns:1fr;}
  .values-grid{grid-template-columns:1fr;}
  .locations-grid{grid-template-columns:1fr;}
  .service-row{grid-template-columns:1fr; gap:12px;}
  .field-row{grid-template-columns:1fr;}
  .footer-inner{grid-template-columns:1fr; gap:28px;}
  nav.links{gap:18px; font-size:0.85rem;}
}

@media (prefers-reduced-motion: reduce){
  html{scroll-behavior:auto;}
}

import React, { useMemo, useState } from "react";
import { motion } from "framer-motion";
import {
  Gamepad2,
  Instagram,
  MessagesSquare,
  ShoppingCart,
  ShieldCheck,
  BadgeCheck,
  PhoneCall,
  CreditCard,
  CheckCircle2,
  Copy,
  Settings as SettingsIcon
} from "lucide-react";

const CONTACT = {
  shopName: "Delgado Shop",
  ooredooNumber: "+216 21079489",
  whatsappNumber: "21621079489",
  instagramHandle: "70y.f",
  discordInvite: "https://discord.gg/7KVbsVEk",
  location: "Tunisia",
  hours: "Daily 10:00 – 23:00",
};

const PRODUCTS = [
  { id: "gta-basic", title: "GTA V Ready Account – Basic", price: 39, currency: "TND", badge: "Popular", features: ["Story complete", "Starter cash", "Secure email change"], category: "GTA V" },
  { id: "gta-premium", title: "GTA V Ready Account – Premium", price: 79, currency: "TND", badge: "Best Value", features: ["High in‑game cash", "Rare vehicles", "24h priority support"], category: "GTA V" },
  { id: "fivem-setup", title: "FiveM Full Setup (Client)", price: 29, currency: "TND", features: ["Optimized settings", "Pack of recommended servers", "Fix common errors"], category: "FiveM" },
  { id: "fivem-pack", title: "FiveM Graphics & FPS Boost Pack", price: 25, currency: "TND", features: ["Better visuals", "Stable FPS on low spec", "Install guide"], category: "FiveM" },
  { id: "ig-methods", title: "Instagram Growth Methods – Starter Pack", price: 35, currency: "TND", features: ["Ethical growth playbook", "Content hooks & captions", "DM outreach templates"], category: "Instagram" },
  { id: "ig-pro", title: "Instagram Growth – Pro Bundle", price: 69, currency: "TND", features: ["Advanced strategies", "Analytics tracking sheet", "1:1 setup call (15min)"], category: "Instagram" },
];

function classNames(...c) { return c.filter(Boolean).join(" "); }

export default function DelgadoShop() {
  const [selected, setSelected] = useState(null);
  const [copied, setCopied] = useState(false);

  const whatsappBase = useMemo(() => `https://wa.me/${CONTACT.whatsappNumber}`, []);

  const onCopy = async () => { try { await navigator.clipboard.writeText(CONTACT.ooredooNumber); setCopied(true); setTimeout(() => setCopied(false), 1400); } catch {} };

  const whatsappCheckoutUrl = (product) => {
    const text = encodeURIComponent(`Hello ${CONTACT.shopName}! I want to buy: ${product.title} (ID: ${product.id}) via Ooredoo ticket. My proof will follow.`);
    return `${whatsappBase}?text=${text}`;
  };

  return (
    <div className="min-h-screen bg-neutral-950 text-white">
      <header className="sticky top-0 z-40 backdrop-blur supports-[backdrop-filter]:bg-neutral-950/70 bg-neutral-950/60 border-b border-white/10">
        <div className="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 py-3 flex items-center justify-between">
          <a href="#" className="flex items-center gap-2">
            <div className="size-9 rounded-2xl bg-gradient-to-br from-emerald-400 to-emerald-700 grid place-items-center shadow-lg shadow-emerald-500/30">
              <Gamepad2 className="size-5" />
            </div>
            <div className="leading-tight">
              <p className="font-semibold tracking-wide">{CONTACT.shopName}</p>
              <p className="text-xs text-white/60">GTA V • FiveM • Instagram</p>
            </div>
          </a>
          <nav className="hidden md:flex items-center gap-6 text-sm">
            <a href="#products" className="hover:text-emerald-300">Products</a>
            <a href="#how" className="hover:text-emerald-300">How to buy</a>
            <a href="#contact" className="hover:text-emerald-300">Contact</a>
          </nav>
          <div className="flex items-center gap-2">
            <a href={whatsappBase} className="inline-flex items-center gap-2 rounded-2xl bg-emerald-500/90 hover:bg-emerald-400 px-4 py-2 text-sm font-semibold shadow-lg shadow-emerald-500/30">
              <MessagesSquare className="size-4" /> Chat WhatsApp
            </a>
          </div>
        </div>
      </header>
      <section className="relative overflow-hidden">
        <div className="absolute inset-0 bg-[radial-gradient(circle_at_20%_20%,rgba(16,185,129,0.15),transparent_40%),radial-gradient(circle_at_80%_20%,rgba(59,130,246,0.12),transparent_40%)]" />
        <div className="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 py-16 sm:py-24">
          <motion.div initial={{ opacity: 0, y: 20 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.6 }} className="grid lg:grid-cols-2 gap-10 items-center">
            <div>
              <h1 className="text-3xl sm:text-5xl font-black leading-tight">
                Level up fast with
                <span className="block text-transparent bg-clip-text bg-gradient-to-r from-emerald-400 to-blue-400">GTA V • FiveM • Instagram</span>
              </h1>
              <p className="mt-4 text-white/80 max-w-xl">
                Trusted digital services and guides. Pay easily using <span className="font-semibold">Ooredoo Tunisian ticket</span> and receive your product quickly via WhatsApp or Discord.
              </p>
              <div className="mt-6 flex flex-wrap gap-3">
                <a href="#products" className="rounded-2xl bg-white text-neutral-950 px-5 py-3 font-semibold hover:bg-white/90">Browse Products</a>
                <a href="#how" className="rounded-2xl border border-white/20 px-5 py-3 font-semibold hover:border-white/40">How to Buy</a>
              </div>
              <div className="mt-6 flex flex-wrap items-center gap-5 text-xs text-white/60">
                <span className="inline-flex items-center gap-1"><ShieldCheck className="size-4"/> Trusted seller</span>
                <span className="inline-flex items-center gap-1"><BadgeCheck className="size-4"/> Fast delivery</span>
                <span className="inline-flex items-center gap-1"><CreditCard className="size-4"/> Ooredoo ticket accepted</span>
              </div>
              <div className="mt-4 flex gap-3">
                <a href={CONTACT.discordInvite} className="rounded-xl bg-indigo-600 hover:bg-indigo-500 px-5 py-3 font-semibold inline-flex items-center gap-2">Join Discord</a>
                <a href={`https://instagram.com/${CONTACT.instagramHandle}`} className="rounded-xl border border-white/20 hover:border-white/40 px-5 py-3 font-semibold inline-flex items-center gap-2">Follow on Instagram</a>
              </div>
            </div>
            <div className="relative">
              <div className="absolute -inset-6 bg-gradient-to-tr from-emerald-500/20 to-blue-500/20 blur-2xl rounded-3xl" />
              <div className="relative rounded-3xl border border-white/10 bg-neutral-900/60 p-6 sm:p-8 shadow-2xl">
                <div className="grid grid-cols-2 gap-4">
                  {[{ title: "GTA V Ready", icon: <Gamepad2 className="size-5" /> }, { title: "FiveM Setup", icon: <SettingsIcon /> }, { title: "IG Methods", icon: <Instagram className="size-5" /> }, { title: "Support", icon: <PhoneCall className="size-5" /> }].map((c) => (
                    <div key={c.title} className="rounded-2xl bg-neutral-800/80 border border-white/10 p-4 sm:p-5">
                      <div className="mb-3">{c.icon}</div>
                      <p className="text-sm font-semibold">{c.title}</p>
                      <p className="text-xs text-white/60">Instant guidance</p>
                    </div>
                  ))}
                </div>
                <div className="mt-6 flex items-center justify-between rounded-2xl bg-neutral-800/80 border border-white/10 p-4">
                  <div className="text-sm">
                    <p className="font-semibold">Pay by Ooredoo ticket</p>
                    <p className="text-white/60">Number: {CONTACT.ooredooNumber}</p>
                  </div>
                  <button onClick={onCopy} className="inline-flex items-center gap-2 rounded-xl bg-emerald-500/90 hover:bg-emerald-400 px-4 py-2 text-sm font-semibold shadow">
                    <Copy className="size-4" /> {copied ? "Copied!" : "Copy"}
                  </button>
                </div>
              </div>
            </div>
          </motion.div>
        </div>
      </section>
      {/* ... rest of the code stays unchanged ... */}
    </div>
  );
}

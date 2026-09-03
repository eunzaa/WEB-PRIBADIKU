// App.jsx
import React, { useState, useEffect } from 'react';
import { motion, AnimatePresence } from 'framer-motion';
import { 
  Menu, X, Home, User, FileText, Image, 
  BookOpen, Share2, Mail, Star, ChevronRight,
  Instagram, Youtube, Facebook, Linkedin, Twitter,
  Phone, MapPin, Send, Download, Search, Filter,
  Github, Globe, Award, Briefcase, GraduationCap,
  Heart, Sparkles, Smile, Coffee
} from 'lucide-react';

// ============ DATA ============
const data = {
  name: "Adelia Hafizatunnisa",
  title: "Pelajar",
  tagline: "Sekarang belajar di SMKN 42 Jakarta",
  about: "Halo! Saya Adelia, seorang pelajar yang memiliki passion di dunia desain dan teknologi. Saya suka mengeksplorasi hal-hal baru dan menciptakan karya yang bermanfaat. Dengan semangat belajar yang tinggi, saya terus mengembangkan skill di bidang desain grafis, fotografi, dan pengembangan web.",
  stats: [
    { label: "Pengalaman", value: "2+" },
    { label: "Project", value: "15+" },
    { label: "Karya", value: "30+" },
    { label: "Klien", value: "10+" }
  ],
  education: [
    { year: "2024 - Sekarang", title: "SMKN 42 Jakarta", desc: "Jurusan Multimedia" },
    { year: "2021 - 2024", title: "SMPN 123 Jakarta", desc: "Lulus dengan predikat baik" }
  ],
  experience: [
    { year: "2025", title: "Magang Desain Grafis", desc: "PT Kreatif Digital" },
    { year: "2024", title: "Freelance Fotografer", desc: "Berbagai event sekolah" }
  ],
  skills: ["Desain Grafis", "Fotografi", "Videografi", "UI/UX Design", "HTML/CSS", "JavaScript"],
  certifications: ["Sertifikat Adobe Photoshop", "Sertifikat Videografi"],
  organizations: ["Ketua Ekstrakurikuler Fotografi", "Anggota OSIS"],
  socials: {
    instagram: "https://instagram.com/adelia",
    tiktok: "https://tiktok.com/@adelia",
    youtube: "https://youtube.com/@adelia",
    facebook: "https://facebook.com/adelia",
    linkedin: "https://linkedin.com/in/adelia",
    twitter: "https://twitter.com/adelia",
    whatsapp: "https://wa.me/6281234567890"
  },
  contact: {
    email: "adelia@email.com",
    phone: "+62 812-3456-7890",
    location: "Jakarta, Indonesia"
  },
  testimonials: [
    { name: "Rina", role: "Klien", text: "Karya Adelia sangat kreatif dan profesional!", rating: 5 },
    { name: "Budi", role: "Teman", text: "Adelia orangnya ramah dan sangat berbakat.", rating: 5 },
    { name: "Siti", role: "Guru", text: "Siswa yang tekun dan selalu berkarya.", rating: 4 }
  ]
};

const works = [
  { id: 1, title: "Poster Kreatif", category: "Desain", image: "/api/placeholder/400/300", desc: "Poster untuk event sekolah" },
  { id: 2, title: "Photo Series", category: "Foto", image: "/api/placeholder/400/300", desc: "Series foto tentang alam" },
  { id: 3, title: "Project Website", category: "Project", image: "/api/placeholder/400/300", desc: "Website portfolio sederhana" },
  { id: 4, title: "Video Animasi", category: "Video", image: "/api/placeholder/400/300", desc: "Animasi pendek 2D" },
  { id: 5, title: "Logo Design", category: "Desain", image: "/api/placeholder/400/300", desc: "Logo untuk bisnis lokal" },
  { id: 6, title: "Foto Event", category: "Foto", image: "/api/placeholder/400/300", desc: "Dokumentasi event sekolah" }
];

const photos = [
  { id: 1, title: "Sunset di Pantai", src: "/api/placeholder/400/500" },
  { id: 2, title: "Kota di Malam Hari", src: "/api/placeholder/400/500" },
  { id: 3, title: "Potret Alam", src: "/api/placeholder/400/500" },
  { id: 4, title: "Arsitektur", src: "/api/placeholder/400/500" },
  { id: 5, title: "Makro", src: "/api/placeholder/400/500" }
];

const articles = [
  { id: 1, title: "Tips Desain Grafis untuk Pemula", category: "Desain", date: "15 Jan 2026", summary: "Panduan dasar memulai desain grafis", image: "/api/placeholder/400/300" },
  { id: 2, title: "Fotografi dengan Smartphone", category: "Fotografi", date: "10 Feb 2026", summary: "Tips mengambil foto bagus dengan HP", image: "/api/placeholder/400/300" }
];

// ============ KOMPONEN ============

const Navbar = ({ active, setActive, isOpen, setIsOpen }) => {
  const menuItems = [
    { id: 'home', label: 'Beranda', icon: Home },
    { id: 'about', label: 'Tentang', icon: User },
    { id: 'cv', label: 'CV', icon: FileText },
    { id: 'works', label: 'Karya', icon: Image },
    { id: 'photos', label: 'Foto', icon: Image },
    { id: 'articles', label: 'Artikel', icon: BookOpen },
    { id: 'socials', label: 'Sosial Media', icon: Share2 },
    { id: 'contact', label: 'Kontak', icon: Mail },
    { id: 'testimonials', label: 'Testimoni', icon: Star }
  ];

  const scrollToSection = (id) => {
    const el = document.getElementById(id);
    if (el) {
      el.scrollIntoView({ behavior: 'smooth', block: 'start' });
      setActive(id);
      setIsOpen(false);
    }
  };

  return (
    <>
      <motion.nav 
        initial={{ y: -100 }}
        animate={{ y: 0 }}
        className="fixed top-0 left-0 right-0 z-50 bg-white/80 backdrop-blur-lg shadow-sm"
      >
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex justify-between items-center h-16">
            <motion.div 
              whileHover={{ scale: 1.05 }}
              className="flex items-center gap-2 cursor-pointer"
              onClick={() => scrollToSection('home')}
            >
              <Sparkles className="w-6 h-6 text-purple-500" />
              <span className="font-bold text-lg bg-gradient-to-r from-purple-500 to-pink-400 bg-clip-text text-transparent">
                {data.name.split(' ')[0]}
              </span>
            </motion.div>

            {/* Desktop Menu */}
            <div className="hidden lg:flex items-center gap-1">
              {menuItems.map((item) => (
                <motion.button
                  key={item.id}
                  whileHover={{ scale: 1.05 }}
                  whileTap={{ scale: 0.95 }}
                  onClick={() => scrollToSection(item.id)}
                  className={`px-3 py-2 rounded-full text-sm transition-all duration-300 flex items-center gap-1.5 ${
                    active === item.id 
                      ? 'bg-purple-100 text-purple-600 font-medium' 
                      : 'text-gray-600 hover:bg-gray-100'
                  }`}
                >
                  <item.icon className="w-4 h-4" />
                  {item.label}
                </motion.button>
              ))}
              <motion.a
                whileHover={{ scale: 1.05 }}
                whileTap={{ scale: 0.95 }}
                href="#contact"
                className="ml-2 px-4 py-2 rounded-full bg-gradient-to-r from-purple-500 to-pink-400 text-white text-sm font-medium flex items-center gap-2 shadow-lg shadow-purple-200"
              >
                Let's Talk <ChevronRight className="w-4 h-4" />
              </motion.a>
            </div>

            {/* Mobile Menu Button */}
            <button 
              onClick={() => setIsOpen(!isOpen)}
              className="lg:hidden p-2 rounded-lg hover:bg-gray-100 transition"
            >
              {isOpen ? <X className="w-6 h-6" /> : <Menu className="w-6 h-6" />}
            </button>
          </div>
        </div>
      </motion.nav>

      {/* Mobile Menu */}
      <AnimatePresence>
        {isOpen && (
          <motion.div
            initial={{ opacity: 0, y: -20 }}
            animate={{ opacity: 1, y: 0 }}
            exit={{ opacity: 0, y: -20 }}
            className="fixed inset-x-0 top-16 z-40 bg-white/95 backdrop-blur-lg shadow-xl lg:hidden"
          >
            <div className="p-4 space-y-1 max-h-[calc(100vh-4rem)] overflow-y-auto">
              {menuItems.map((item) => (
                <motion.button
                  key={item.id}
                  whileHover={{ x: 10 }}
                  onClick={() => scrollToSection(item.id)}
                  className={`w-full px-4 py-3 rounded-xl text-left flex items-center gap-3 transition ${
                    active === item.id 
                      ? 'bg-purple-100 text-purple-600 font-medium' 
                      : 'text-gray-600 hover:bg-gray-50'
                  }`}
                >
                  <item.icon className="w-5 h-5" />
                  <span>{item.label}</span>
                </motion.button>
              ))}
              <motion.a
                whileHover={{ x: 10 }}
                href="#contact"
                className="w-full px-4 py-3 rounded-xl bg-gradient-to-r from-purple-500 to-pink-400 text-white font-medium flex items-center justify-center gap-2 mt-4"
              >
                Let's Talk <ChevronRight className="w-4 h-4" />
              </motion.a>
            </div>
          </motion.div>
        )}
      </AnimatePresence>
    </>
  );
};

// Section: Home
const HomeSection = ({ setActive }) => {
  return (
    <motion.section
      id="home"
      initial={{ opacity: 0 }}
      whileInView={{ opacity: 1 }}
      viewport={{ once: true }}
      className="min-h-screen flex items-center pt-16"
    >
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
        <div className="flex flex-col lg:flex-row items-center gap-12">
          <motion.div 
            initial={{ x: -50, opacity: 0 }}
            animate={{ x: 0, opacity: 1 }}
            transition={{ delay: 0.2 }}
            className="flex-1 text-center lg:text-left"
          >
            <motion.div
              animate={{ y: [0, -10, 0] }}
              transition={{ duration: 2, repeat: Infinity }}
              className="inline-block px-4 py-2 rounded-full bg-purple-100 text-purple-600 text-sm font-medium mb-4"
            >
              <Smile className="w-4 h-4 inline mr-2" />
              Halo, saya
            </motion.div>
            
            <h1 className="text-4xl sm:text-5xl lg:text-6xl font-bold text-gray-800 mb-4">
              {data.name}
            </h1>
            
            <div className="text-2xl sm:text-3xl text-gray-600 mb-4">
              {data.title}
            </div>
            
            <p className="text-xl text-gray-500 mb-8 flex items-center gap-2 justify-center lg:justify-start">
              <span className="inline-block animate-bounce">👋</span>
              {data.tagline}
            </p>

            <div className="flex flex-wrap gap-4 justify-center lg:justify-start">
              <motion.a
                whileHover={{ scale: 1.05 }}
                whileTap={{ scale: 0.95 }}
                href="#works"
                onClick={() => setActive('works')}
                className="px-8 py-3 rounded-full bg-gradient-to-r from-purple-500 to-pink-400 text-white font-medium shadow-lg shadow-purple-200 flex items-center gap-2"
              >
                Lihat Karya <ChevronRight className="w-4 h-4" />
              </motion.a>
              <motion.a
                whileHover={{ scale: 1.05 }}
                whileTap={{ scale: 0.95 }}
                href="#contact"
                onClick={() => setActive('contact')}
                className="px-8 py-3 rounded-full border-2 border-purple-300 text-purple-600 font-medium hover:bg-purple-50 transition"
              >
                Hubungi Saya
              </motion.a>
            </div>
          </motion.div>

          <motion.div
            initial={{ scale: 0, rotate: -10 }}
            animate={{ scale: 1, rotate: 0 }}
            transition={{ delay: 0.3, type: 'spring' }}
            className="flex-1 flex justify-center"
          >
            <div className="relative">
              <div className="w-64 h-64 sm:w-80 sm:h-80 rounded-full bg-gradient-to-br from-purple-200 to-pink-200 p-1">
                <div className="w-full h-full rounded-full bg-white flex items-center justify-center overflow-hidden">
                  <img 
                    src="/api/placeholder/320/320" 
                    alt="Profile" 
                    className="w-full h-full object-cover"
                  />
                </div>
              </div>
              <motion.div
                animate={{ rotate: 360 }}
                transition={{ duration: 20, repeat: Infinity, ease: 'linear' }}
                className="absolute -top-4 -right-4 w-12 h-12 rounded-full bg-yellow-200 flex items-center justify-center text-2xl"
              >
                ⭐
              </motion.div>
              <motion.div
                animate={{ y: [0, -10, 0] }}
                transition={{ duration: 2, repeat: Infinity }}
                className="absolute -bottom-2 -left-2 w-10 h-10 rounded-full bg-pink-200 flex items-center justify-center text-xl"
              >
                🎨
              </motion.div>
            </div>
          </motion.div>
        </div>
      </div>
    </motion.section>
  );
};

// Section: About
const AboutSection = () => {
  return (
    <motion.section
      id="about"
      initial={{ opacity: 0, y: 50 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true }}
      className="py-20 bg-white/50"
    >
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <motion.div
          initial={{ opacity: 0, y: 20 }}
          whileInView={{ opacity: 1, y: 0 }}
          viewport={{ once: true }}
          className="text-center mb-12"
        >
          <h2 className="text-3xl sm:text-4xl font-bold text-gray-800">
            Tentang <span className="bg-gradient-to-r from-purple-500 to-pink-400 bg-clip-text text-transparent">Saya</span>
          </h2>
          <div className="w-20 h-1 bg-gradient-to-r from-purple-500 to-pink-400 mx-auto mt-4 rounded-full" />
        </motion.div>

        <div className="flex flex-col lg:flex-row gap-12 items-center">
          <motion.div
            initial={{ scale: 0.8, opacity: 0 }}
            whileInView={{ scale: 1, opacity: 1 }}
            viewport={{ once: true }}
            className="flex-1 flex justify-center"
          >
            <div className="relative">
              <div className="w-64 h-64 rounded-2xl overflow-hidden shadow-xl">
                <img src="/api/placeholder/400/400" alt="About" className="w-full h-full object-cover" />
              </div>
              <div className="absolute -bottom-4 -right-4 bg-white rounded-xl shadow-lg p-3 flex items-center gap-2">
                <Coffee className="w-5 h-5 text-yellow-500" />
                <span className="text-sm font-medium">Suka Kopi</span>
              </div>
            </div>
          </motion.div>

          <motion.div
            initial={{ x: 50, opacity: 0 }}
            whileInView={{ x: 0, opacity: 1 }}
            viewport={{ once: true }}
            className="flex-1"
          >
            <p className="text-lg text-gray-600 leading-relaxed mb-6">
              {data.about}
            </p>
            
            <div className="grid grid-cols-2 sm:grid-cols-4 gap-4">
              {data.stats.map((stat, i) => (
                <motion.div
                  key={i}
                  whileHover={{ y: -5 }}
                  className="bg-white rounded-xl p-4 text-center shadow-sm border border-gray-100"
                >
                  <div className="text-2xl font-bold text-purple-500">{stat.value}</div>
                  <div className="text-sm text-gray-500">{stat.label}</div>
                </motion.div>
              ))}
            </div>

            <div className="mt-6 flex flex-wrap gap-3">
              {['🎯', '💡', '🚀', '✨'].map((emoji, i) => (
                <span key={i} className="text-2xl">{emoji}</span>
              ))}
            </div>
          </motion.div>
        </div>
      </div>
    </motion.section>
  );
};

// Section: CV
const CVSection = () => {
  return (
    <motion.section
      id="cv"
      initial={{ opacity: 0, y: 50 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true }}
      className="py-20"
    >
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-12">
          <h2 className="text-3xl sm:text-4xl font-bold text-gray-800">
            CV <span className="bg-gradient-to-r from-purple-500 to-pink-400 bg-clip-text text-transparent">Saya</span>
          </h2>
          <div className="w-20 h-1 bg-gradient-to-r from-purple-500 to-pink-400 mx-auto mt-4 rounded-full" />
        </div>

        <div className="grid md:grid-cols-2 gap-8">
          <motion.div
            initial={{ x: -30, opacity: 0 }}
            whileInView={{ x: 0, opacity: 1 }}
            viewport={{ once: true }}
            className="space-y-6"
          >
            <div className="bg-white rounded-2xl p-6 shadow-sm border border-gray-100">
              <h3 className="text-xl font-semibold text-gray-800 mb-4 flex items-center gap-2">
                <GraduationCap className="w-5 h-5 text-purple-500" />
                Pendidikan
              </h3>
              {data.education.map((edu, i) => (
                <div key={i} className="border-l-4 border-purple-300 pl-4 mb-4 last:mb-0">
                  <div className="text-sm text-purple-500 font-medium">{edu.year}</div>
                  <div className="font-semibold text-gray-800">{edu.title}</div>
                  <div className="text-gray-500 text-sm">{edu.desc}</div>
                </div>
              ))}
            </div>

            <div className="bg-white rounded-2xl p-6 shadow-sm border border-gray-100">
              <h3 className="text-xl font-semibold text-gray-800 mb-4 flex items-center gap-2">
                <Briefcase className="w-5 h-5 text-pink-400" />
                Pengalaman
              </h3>
              {data.experience.map((exp, i) => (
                <div key={i} className="border-l-4 border-pink-300 pl-4 mb-4 last:mb-0">
                  <div className="text-sm text-pink-500 font-medium">{exp.year}</div>
                  <div className="font-semibold text-gray-800">{exp.title}</div>
                  <div className="text-gray-500 text-sm">{exp.desc}</div>
                </div>
              ))}
            </div>
          </motion.div>

          <motion.div
            initial={{ x: 30, opacity: 0 }}
            whileInView={{ x: 0, opacity: 1 }}
            viewport={{ once: true }}
            className="space-y-6"
          >
            <div className="bg-white rounded-2xl p-6 shadow-sm border border-gray-100">
              <h3 className="text-xl font-semibold text-gray-800 mb-4 flex items-center gap-2">
                <Award className="w-5 h-5 text-yellow-500" />
                Keahlian
              </h3>
              <div className="flex flex-wrap gap-2">
                {data.skills.map((skill, i) => (
                  <span key={i} className="px-3 py-1.5 rounded-full bg-purple-100 text-purple-600 text-sm font-medium">
                    {skill}
                  </span>
                ))}
              </div>
            </div>

            <div className="bg-white rounded-2xl p-6 shadow-sm border border-gray-100">
              <h3 className="text-xl font-semibold text-gray-800 mb-4 flex items-center gap-2">
                <Globe className="w-5 h-5 text-blue-400" />
                Sertifikasi & Organisasi
              </h3>
              <ul className="space-y-2">
                {data.certifications.map((cert, i) => (
                  <li key={i} className="flex items-center gap-2 text-gray-600">
                    <span className="w-1.5 h-1.5 rounded-full bg-purple-400" />
                    {cert}
                  </li>
                ))}
                {data.organizations.map((org, i) => (
                  <li key={i} className="flex items-center gap-2 text-gray-600">
                    <span className="w-1.5 h-1.5 rounded-full bg-pink-400" />
                    {org}
                  </li>
                ))}
              </ul>
            </div>

            <motion.a
              whileHover={{ scale: 1.02 }}
              whileTap={{ scale: 0.98 }}
              href="#"
              className="block text-center px-6 py-3 rounded-xl bg-gradient-to-r from-purple-500 to-pink-400 text-white font-medium shadow-lg shadow-purple-200 flex items-center justify-center gap-2"
            >
              <Download className="w-5 h-5" />
              Download CV
            </motion.a>
          </motion.div>
        </div>
      </div>
    </motion.section>
  );
};

// Section: Works
const WorksSection = () => {
  const [filter, setFilter] = useState('Semua');
  const categories = ['Semua', ...new Set(works.map(w => w.category))];
  const filtered = filter === 'Semua' ? works : works.filter(w => w.category === filter);

  return (
    <motion.section
      id="works"
      initial={{ opacity: 0, y: 50 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true }}
      className="py-20 bg-white/50"
    >
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-12">
          <h2 className="text-3xl sm:text-4xl font-bold text-gray-800">
            Hasil <span className="bg-gradient-to-r from-purple-500 to-pink-400 bg-clip-text text-transparent">Karya</span>
          </h2>
          <div className="w-20 h-1 bg-gradient-to-r from-purple-500 to-pink-400 mx-auto mt-4 rounded-full" />
        </div>

        <div className="flex flex-wrap gap-2 justify-center mb-8">
          {categories.map((cat) => (
            <motion.button
              key={cat}
              whileHover={{ scale: 1.05 }}
              whileTap={{ scale: 0.95 }}
              onClick={() => setFilter(cat)}
              className={`px-4 py-2 rounded-full text-sm font-medium transition ${
                filter === cat 
                  ? 'bg-purple-500 text-white shadow-lg shadow-purple-200' 
                  : 'bg-white text-gray-600 hover:bg-gray-100 border border-gray-200'
              }`}
            >
              {cat}
            </motion.button>
          ))}
        </div>

        <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
          {filtered.map((work) => (
            <motion.div
              key={work.id}
              layout
              initial={{ opacity: 0, scale: 0.9 }}
              animate={{ opacity: 1, scale: 1 }}
              exit={{ opacity: 0, scale: 0.9 }}
              whileHover={{ y: -10 }}
              className="group bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300"
            >
              <div className="relative overflow-hidden aspect-[4/3]">
                <img 
                  src={work.image} 
                  alt={work.title}
                  className="w-full h-full object-cover group-hover:scale-110 transition duration-500"
                />
                <div className="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent opacity-0 group-hover:opacity-100 transition duration-300 flex items-end p-4">
                  <span className="text-white text-sm font-medium bg-white/20 backdrop-blur-sm px-3 py-1 rounded-full">
                    {work.category}
                  </span>
                </div>
              </div>
              <div className="p-4">
                <h3 className="font-semibold text-gray-800">{work.title}</h3>
                <p className="text-sm text-gray-500">{work.desc}</p>
              </div>
            </motion.div>
          ))}
        </div>
      </div>
    </motion.section>
  );
};

// Section: Photos
const PhotosSection = () => {
  return (
    <motion.section
      id="photos"
      initial={{ opacity: 0, y: 50 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true }}
      className="py-20"
    >
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-12">
          <h2 className="text-3xl sm:text-4xl font-bold text-gray-800">
            Galeri <span className="bg-gradient-to-r from-purple-500 to-pink-400 bg-clip-text text-transparent">Foto</span>
          </h2>
          <div className="w-20 h-1 bg-gradient-to-r from-purple-500 to-pink-400 mx-auto mt-4 rounded-full" />
        </div>

        <div className="columns-1 sm:columns-2 lg:columns-3 gap-6 space-y-6">
          {photos.map((photo) => (
            <motion.div
              key={photo.id}
              whileHover={{ scale: 1.02 }}
              className="break-inside-avoid group relative rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300"
            >
              <img 
                src={photo.src} 
                alt={photo.title}
                className="w-full h-auto object-cover"
                loading="lazy"
              />
              <div className="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition duration-300 flex items-end p-4">
                <p className="text-white text-sm font-medium">{photo.title}</p>
              </div>
            </motion.div>
          ))}
        </div>
      </div>
    </motion.section>
  );
};

// Section: Articles
const ArticlesSection = () => {
  const [search, setSearch] = useState('');
  const filtered = articles.filter(a => 
    a.title.toLowerCase().includes(search.toLowerCase()) ||
    a.category.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <motion.section
      id="articles"
      initial={{ opacity: 0, y: 50 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true }}
      className="py-20 bg-white/50"
    >
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-12">
          <h2 className="text-3xl sm:text-4xl font-bold text-gray-800">
            <span className="bg-gradient-to-r from-purple-500 to-pink-400 bg-clip-text text-transparent">Artikel</span>
          </h2>
          <div className="w-20 h-1 bg-gradient-to-r from-purple-500 to-pink-400 mx-auto mt-4 rounded-full" />
        </div>

        <div className="max-w-md mx-auto mb-8">
          <div className="relative">
            <Search className="absolute left-3 top-1/2 -translate-y-1/2 w-5 h-5 text-gray-400" />
            <input
              type="text"
              placeholder="Cari artikel..."
              value={search}
              onChange={(e) => setSearch(e.target.value)}
              className="w-full pl-10 pr-4 py-3 rounded-xl border border-gray-200 focus:border-purple-400 focus:ring-2 focus:ring-purple-200 outline-none transition"
            />
          </div>
        </div>

        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          {filtered.map((article) => (
            <motion.div
              key={article.id}
              whileHover={{ y: -10 }}
              className="bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300"
            >
              <img src={article.image} alt={article.title} className="w-full h-48 object-cover" />
              <div className="p-5">
                <div className="flex items-center gap-2 text-sm text-gray-500 mb-2">
                  <span className="px-2 py-0.5 rounded-full bg-purple-100 text-purple-600 text-xs font-medium">
                    {article.category}
                  </span>
                  <span>{article.date}</span>
                </div>
                <h3 className="font-semibold text-gray-800 mb-2 line-clamp-2">{article.title}</h3>
                <p className="text-sm text-gray-500 line-clamp-2">{article.summary}</p>
                <motion.button
                  whileHover={{ x: 5 }}
                  className="mt-3 text-purple-500 font-medium text-sm flex items-center gap-1"
                >
                  Baca Selengkapnya <ChevronRight className="w-4 h-4" />
                </motion.button>
              </div>
            </motion.div>
          ))}
        </div>
      </div>
    </motion.section>
  );
};

// Section: Socials
const SocialsSection = () => {
  const socialIcons = {
    instagram: Instagram,
    tiktok: Share2,
    youtube: Youtube,
    facebook: Facebook,
    linkedin: Linkedin,
    twitter: Twitter,
    whatsapp: Phone
  };

  return (
    <motion.section
      id="socials"
      initial={{ opacity: 0, y: 50 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true }}
      className="py-20"
    >
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-12">
          <h2 className="text-3xl sm:text-4xl font-bold text-gray-800">
            <span className="bg-gradient-to-r from-purple-500 to-pink-400 bg-clip-text text-transparent">Media Sosial</span>
          </h2>
          <div className="w-20 h-1 bg-gradient-to-r from-purple-500 to-pink-400 mx-auto mt-4 rounded-full" />
        </div>

        <div className="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-4 max-w-3xl mx-auto">
          {Object.entries(data.socials).map(([key, url]) => {
            const Icon = socialIcons[key] || Share2;
            return (
              <motion.a
                key={key}
                whileHover={{ y: -5, scale: 1.05 }}
                whileTap={{ scale: 0.95 }}
                href={url}
                target="_blank"
                rel="noopener noreferrer"
                className="bg-white rounded-2xl p-4 text-center shadow-sm border border-gray-100 hover:shadow-lg transition-all duration-300 flex flex-col items-center gap-2"
              >
                <div className="w-12 h-12 rounded-full bg-gradient-to-br from-purple-100 to-pink-100 flex items-center justify-center">
                  <Icon className="w-6 h-6 text-purple-500" />
                </div>
                <span className="text-sm font-medium text-gray-700 capitalize">{key}</span>
              </motion.a>
            );
          })}
        </div>
      </div>
    </motion.section>
  );
};

// Section: Contact
const ContactSection = () => {
  return (
    <motion.section
      id="contact"
      initial={{ opacity: 0, y: 50 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true }}
      className="py-20 bg-white/50"
    >
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-12">
          <h2 className="text-3xl sm:text-4xl font-bold text-gray-800">
            <span className="bg-gradient-to-r from-purple-500 to-pink-400 bg-clip-text text-transparent">Kontak</span>
          </h2>
          <div className="w-20 h-1 bg-gradient-to-r from-purple-500 to-pink-400 mx-auto mt-4 rounded-full" />
        </div>

        <div

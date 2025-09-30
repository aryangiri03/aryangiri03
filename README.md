import React, { useState, useEffect } from 'react';
import { Github, Linkedin, Code2, Database, Brain, Rocket, Mail, Zap, Star, Terminal, Coffee } from 'lucide-react';

export default function FuturisticReadme() {
  const [mousePos, setMousePos] = useState({ x: 0, y: 0 });
  const [currentFact, setCurrentFact] = useState(0);

  const facts = [
    "Code maestro weaving Python & C spells 🐍",
    "Tech geek sculpting digital wonders 🌟",
    "Unleashing magic in the tech cosmos! ✨",
    "Data whisperer turning chaos into insights 📊"
  ];

  useEffect(() => {
    const interval = setInterval(() => {
      setCurrentFact((prev) => (prev + 1) % facts.length);
    }, 3000);
    return () => clearInterval(interval);
  }, []);

  const handleMouseMove = (e) => {
    const rect = e.currentTarget.getBoundingClientRect();
    setMousePos({
      x: e.clientX - rect.left,
      y: e.clientY - rect.top,
    });
  };

  const skills = [
    { name: 'Python', icon: '🐍', color: 'from-blue-400 to-yellow-400', level: 95 },
    { name: 'C/C++', icon: '⚡', color: 'from-purple-400 to-pink-400', level: 90 },
    { name: 'JavaScript', icon: '💛', color: 'from-yellow-300 to-orange-400', level: 85 },
    { name: 'Data Science', icon: '📊', color: 'from-green-400 to-cyan-400', level: 88 },
    { name: 'Machine Learning', icon: '🤖', color: 'from-indigo-400 to-purple-500', level: 82 },
    { name: 'Web Dev', icon: '🌐', color: 'from-pink-400 to-rose-400', level: 87 },
  ];

  const tools = [
    { name: 'AWS', logo: '☁️' },
    { name: 'Git', logo: '📦' },
    { name: 'Flutter', logo: '📱' },
    { name: 'Tailwind', logo: '🎨' },
    { name: 'SQL', logo: '🗃️' },
    { name: 'Figma', logo: '🎭' },
  ];

  return (
    <div 
      className="min-h-screen bg-gradient-to-br from-gray-900 via-purple-900 to-black text-white overflow-hidden relative"
      onMouseMove={handleMouseMove}
    >
      {/* Animated background grid */}
      <div className="absolute inset-0 opacity-20">
        <div className="absolute inset-0" style={{
          backgroundImage: 'linear-gradient(rgba(139, 92, 246, 0.3) 1px, transparent 1px), linear-gradient(90deg, rgba(139, 92, 246, 0.3) 1px, transparent 1px)',
          backgroundSize: '50px 50px',
          animation: 'gridMove 20s linear infinite'
        }}></div>
      </div>

      {/* Floating particles */}
      <div className="absolute inset-0 overflow-hidden pointer-events-none">
        {[...Array(20)].map((_, i) => (
          <div
            key={i}
            className="absolute w-2 h-2 bg-purple-400 rounded-full animate-pulse"
            style={{
              left: `${Math.random() * 100}%`,
              top: `${Math.random() * 100}%`,
              animation: `float ${5 + Math.random() * 10}s ease-in-out infinite`,
              animationDelay: `${Math.random() * 5}s`,
            }}
          ></div>
        ))}
      </div>

      <div className="relative z-10 container mx-auto px-4 py-12 max-w-6xl">
        {/* Hero Section */}
        <div className="text-center mb-16 relative">
          <div className="inline-block mb-6 relative">
            <div className="absolute inset-0 bg-gradient-to-r from-purple-600 to-pink-600 rounded-full blur-2xl opacity-50 animate-pulse"></div>
            <img 
              src="https://user-images.githubusercontent.com/90236635/232446433-d5540fa2-fe28-4bb8-b929-cdb51fe61336.gif" 
              alt="Logo"
              className="relative w-32 h-32 mx-auto rounded-full border-4 border-purple-500 shadow-2xl"
            />
          </div>
          
          <h1 className="text-6xl font-bold mb-4 bg-gradient-to-r from-purple-400 via-pink-400 to-cyan-400 bg-clip-text text-transparent animate-pulse">
            Aryan Giri
          </h1>
          
          <div className="flex items-center justify-center gap-3 mb-6">
            <Terminal className="text-cyan-400 animate-bounce" />
            <p className="text-2xl text-purple-300 font-semibold">Full Stack Developer & Data Scientist</p>
            <Rocket className="text-pink-400 animate-bounce" />
          </div>

          <div className="h-8 flex items-center justify-center">
            <p className="text-lg text-gray-300 italic transition-opacity duration-500">
              {facts[currentFact]}
            </p>
          </div>

          <div className="flex justify-center gap-4 mt-6">
            <img src="https://komarev.com/ghpvc/?username=aryangiri03&label=Profile%20views&color=blueviolet&style=for-the-badge" alt="views" className="animate-pulse" />
          </div>
        </div>

        {/* About Section with Glassmorphism */}
        <div className="mb-16 backdrop-blur-lg bg-white/5 rounded-3xl p-8 border border-purple-500/30 shadow-2xl hover:shadow-purple-500/50 transition-all duration-500 hover:scale-[1.02]">
          <div className="flex items-center gap-3 mb-6">
            <Brain className="text-pink-400 w-8 h-8" />
            <h2 className="text-3xl font-bold bg-gradient-to-r from-purple-400 to-pink-400 bg-clip-text text-transparent">
              About Me
            </h2>
          </div>
          
          <div className="grid md:grid-cols-2 gap-6 text-gray-300">
            <div className="space-y-4">
              <div className="flex items-start gap-3 hover:translate-x-2 transition-transform">
                <Zap className="text-yellow-400 mt-1 flex-shrink-0" />
                <p>Final Year Computer Engineering student passionate about technology and innovation</p>
              </div>
              <div className="flex items-start gap-3 hover:translate-x-2 transition-transform">
                <Database className="text-cyan-400 mt-1 flex-shrink-0" />
                <p>Data Science enthusiast diving deep into analytics and machine learning</p>
              </div>
              <div className="flex items-start gap-3 hover:translate-x-2 transition-transform">
                <Code2 className="text-green-400 mt-1 flex-shrink-0" />
                <p>Proficient in C and Python programming, bringing ideas to life through code</p>
              </div>
            </div>
            <div className="flex items-center justify-center">
              <img 
                src="https://media0.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif?cid=ecf05e47y55lbzk2r7co88iy6b21ywwekg9ip4hy1uudpsu1&ep=v1_gifs_search&rid=giphy.gif&ct=g"
                alt="Coding"
                className="rounded-2xl shadow-2xl border-2 border-purple-500/50 hover:scale-105 transition-transform"
              />
            </div>
          </div>
        </div>

        {/* Skills Grid */}
        <div className="mb-16">
          <h2 className="text-3xl font-bold mb-8 text-center bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent">
            Tech Arsenal
          </h2>
          <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
            {skills.map((skill, idx) => (
              <div
                key={skill.name}
                className="backdrop-blur-lg bg-white/5 rounded-2xl p-6 border border-purple-500/30 hover:border-purple-500 transition-all duration-300 hover:scale-105 hover:shadow-2xl hover:shadow-purple-500/50"
                style={{ animationDelay: `${idx * 0.1}s` }}
              >
                <div className="flex items-center gap-3 mb-4">
                  <span className="text-4xl">{skill.icon}</span>
                  <h3 className="text-xl font-bold text-white">{skill.name}</h3>
                </div>
                <div className="w-full bg-gray-700 rounded-full h-3 overflow-hidden">
                  <div
                    className={`h-full bg-gradient-to-r ${skill.color} rounded-full transition-all duration-1000`}
                    style={{ width: `${skill.level}%` }}
                  ></div>
                </div>
                <p className="text-right text-sm text-gray-400 mt-2">{skill.level}%</p>
              </div>
            ))}
          </div>
        </div>

        {/* Tools Section */}
        <div className="mb-16">
          <h2 className="text-3xl font-bold mb-8 text-center bg-gradient-to-r from-pink-400 to-yellow-400 bg-clip-text text-transparent">
            Tools & Technologies
          </h2>
          <div className="flex flex-wrap justify-center gap-4">
            {tools.map((tool, idx) => (
              <div
                key={tool.name}
                className="backdrop-blur-lg bg-white/5 rounded-xl px-6 py-4 border border-purple-500/30 hover:border-pink-500 transition-all hover:scale-110 hover:shadow-lg hover:shadow-pink-500/50 cursor-pointer"
                style={{ animation: `float ${3 + idx * 0.5}s ease-in-out infinite` }}
              >
                <span className="text-3xl">{tool.logo}</span>
                <p className="text-sm mt-2 text-gray-300">{tool.name}</p>
              </div>
            ))}
          </div>
        </div>

        {/* Quick Facts */}
        <div className="mb-16 grid md:grid-cols-2 gap-6">
          <div className="backdrop-blur-lg bg-gradient-to-br from-purple-500/20 to-pink-500/20 rounded-2xl p-6 border border-purple-500/30 hover:scale-105 transition-transform">
            <Coffee className="text-yellow-400 mb-3" size={32} />
            <h3 className="text-xl font-bold mb-2">Currently Learning</h3>
            <p className="text-gray-300">Deep diving into Advanced Data Science & ML</p>
          </div>
          <div className="backdrop-blur-lg bg-gradient-to-br from-cyan-500/20 to-blue-500/20 rounded-2xl p-6 border border-cyan-500/30 hover:scale-105 transition-transform">
            <Mail className="text-pink-400 mb-3" size={32} />
            <h3 className="text-xl font-bold mb-2">Ask Me About</h3>
            <p className="text-gray-300">Python, C, Web Tech, SQL, Machine Learning</p>
          </div>
        </div>

        {/* Connect Section */}
        <div className="mb-16 backdrop-blur-lg bg-white/5 rounded-3xl p-8 border border-purple-500/30">
          <h2 className="text-3xl font-bold mb-6 text-center bg-gradient-to-r from-purple-400 to-pink-400 bg-clip-text text-transparent">
            Let's Connect
          </h2>
          <div className="flex flex-wrap justify-center gap-4">
            <a href="https://in.linkedin.com/in/aryan-giri-852a0a259" target="_blank" rel="noopener noreferrer"
               className="flex items-center gap-2 backdrop-blur-lg bg-blue-500/20 hover:bg-blue-500/40 px-6 py-3 rounded-xl border border-blue-500/50 hover:scale-110 transition-all">
              <Linkedin /> LinkedIn
            </a>
            <a href="https://github.com/aryangiri03" target="_blank" rel="noopener noreferrer"
               className="flex items-center gap-2 backdrop-blur-lg bg-gray-500/20 hover:bg-gray-500/40 px-6 py-3 rounded-xl border border-gray-500/50 hover:scale-110 transition-all">
              <Github /> GitHub
            </a>
            <a href="mailto:aaryanmgiri@gmail.com"
               className="flex items-center gap-2 backdrop-blur-lg bg-pink-500/20 hover:bg-pink-500/40 px-6 py-3 rounded-xl border border-pink-500/50 hover:scale-110 transition-all">
              <Mail /> Email
            </a>
            <a href="https://stackoverflow.com/users/23186353/aryan-giri" target="_blank" rel="noopener noreferrer"
               className="flex items-center gap-2 backdrop-blur-lg bg-orange-500/20 hover:bg-orange-500/40 px-6 py-3 rounded-xl border border-orange-500/50 hover:scale-110 transition-all">
              <Star /> StackOverflow
            </a>
          </div>
        </div>

        {/* GitHub Stats */}
        <div className="grid md:grid-cols-2 gap-6 mb-16">
          <div className="backdrop-blur-lg bg-white/5 rounded-2xl p-4 border border-purple-500/30 hover:scale-105 transition-transform">
            <img src="https://github-readme-stats.vercel.app/api?username=aryangiri03&show_icons=true&theme=radical&hide_border=true&bg_color=0d1117" alt="stats" className="w-full rounded-lg" />
          </div>
          <div className="backdrop-blur-lg bg-white/5 rounded-2xl p-4 border border-purple-500/30 hover:scale-105 transition-transform">
            <img src="https://github-readme-streak-stats.herokuapp.com/?user=aryangiri03&theme=radical&hide_border=true&background=0d1117" alt="streak" className="w-full rounded-lg" />
          </div>
        </div>

        <div className="backdrop-blur-lg bg-white/5 rounded-2xl p-4 border border-purple-500/30 hover:scale-105 transition-transform">
          <img src="https://github-readme-stats.vercel.app/api/top-langs?username=aryangiri03&show_icons=true&theme=radical&hide_border=true&bg_color=0d1117&layout=compact" alt="languages" className="w-full rounded-lg" />
        </div>

        {/* Footer */}
        <div className="text-center mt-16 text-gray-400">
          <p className="text-sm">✨ Crafted with passion | Let's build the future together 🚀</p>
        </div>
      </div>

      <style jsx>{`
        @keyframes float {
          0%, 100% { transform: translateY(0px) translateX(0px); }
          25% { transform: translateY(-20px) translateX(10px); }
          50% { transform: translateY(-10px) translateX(-10px); }
          75% { transform: translateY(-15px) translateX(5px); }
        }
        @keyframes gridMove {
          0% { transform: translateY(0); }
          100% { transform: translateY(50px); }
        }
      `}</style>
    </div>
  );
}

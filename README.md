"use client"

import type React from "react"

import { Check, Play, Shield, Zap, Globe, Tv, Send, Loader2, Star, Users, Award } from "lucide-react"
import { Button } from "@/components/ui/button"
import { Card, CardContent, CardDescription, CardFooter, CardHeader, CardTitle } from "@/components/ui/card"
import { Badge } from "@/components/ui/badge"
import { Input } from "@/components/ui/input"
import { Label } from "@/components/ui/label"
import { Textarea } from "@/components/ui/textarea"
import { useState, useEffect } from "react"

export default function IPTVSalesPage() {
  const [formData, setFormData] = useState({
    name: "",
    phone: "",
    email: "",
    plan: "Teste Grátis 3h",
    message: "",
  })
  const [isSubmitting, setIsSubmitting] = useState(false)
  const [submitStatus, setSubmitStatus] = useState<"idle" | "success" | "error">("idle")
  const [mousePosition, setMousePosition] = useState({ x: 0, y: 0 })

  useEffect(() => {
    const handleMouseMove = (e: MouseEvent) => {
      setMousePosition({ x: e.clientX, y: e.clientY })
    }
    window.addEventListener("mousemove", handleMouseMove)
    return () => window.removeEventListener("mousemove", handleMouseMove)
  }, [])

  const handleInputChange = (e: React.ChangeEvent<HTMLInputElement | HTMLTextAreaElement | HTMLSelectElement>) => {
    const { name, value } = e.target
    setFormData((prev) => ({
      ...prev,
      [name]: value,
    }))
  }

  const handleSubmit = async (e: React.FormEvent) => {
    e.preventDefault()
    setIsSubmitting(true)

    try {
      await new Promise((resolve) => setTimeout(resolve, 2000))

      const message = `Olá! Vim pelo site SHARK TV e gostaria de mais informações:
      
Nome: ${formData.name}
WhatsApp: ${formData.phone}
Email: ${formData.email}
Plano de Interesse: ${formData.plan}
${formData.message ? `Mensagem: ${formData.message}` : ""}`

      const whatsappUrl = `http://wa.me/5519971672016?text=${encodeURIComponent(message)}`
      window.open(whatsappUrl, "_blank")

      setSubmitStatus("success")
      setFormData({
        name: "",
        phone: "",
        email: "",
        plan: "Teste Grátis 3h",
        message: "",
      })
    } catch (error) {
      setSubmitStatus("error")
    } finally {
      setIsSubmitting(false)
      setTimeout(() => setSubmitStatus("idle"), 3000)
    }
  }

  const isFormValid = formData.name && formData.phone && formData.email

  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-900 via-purple-900 to-slate-900 relative overflow-hidden">
      {/* Animated Background Elements */}
      <div className="absolute inset-0 overflow-hidden pointer-events-none">
        <div className="absolute -top-40 -right-40 w-80 h-80 bg-purple-500/20 rounded-full blur-3xl animate-pulse"></div>
        <div className="absolute -bottom-40 -left-40 w-80 h-80 bg-blue-500/20 rounded-full blur-3xl animate-pulse delay-1000"></div>
        <div className="absolute top-1/2 left-1/2 w-60 h-60 bg-pink-500/10 rounded-full blur-3xl animate-bounce delay-500"></div>
      </div>

      {/* Floating Elements */}
      <div className="absolute inset-0 pointer-events-none">
        {[...Array(20)].map((_, i) => (
          <div
            key={i}
            className="absolute w-2 h-2 bg-white/10 rounded-full animate-pulse"
            style={{
              left: `${Math.random() * 100}%`,
              top: `${Math.random() * 100}%`,
              animationDelay: `${Math.random() * 3}s`,
              animationDuration: `${2 + Math.random() * 3}s`,
            }}
          />
        ))}
      </div>

      {/* Header */}
      <header className="container mx-auto px-4 py-6 relative z-10">
        <nav className="flex items-center justify-between backdrop-blur-sm bg-white/5 rounded-2xl px-6 py-4 border border-white/10">
          <div className="flex items-center space-x-3 group">
            <div className="relative">
              <img
                src="/images/sharktv-logo.png"
                alt="Shark TV Logo"
                className="h-12 w-12 object-contain transition-transform group-hover:scale-110 group-hover:rotate-12"
              />
              <div className="absolute inset-0 bg-gradient-to-r from-blue-500 to-purple-500 rounded-full blur-lg opacity-0 group-hover:opacity-30 transition-opacity"></div>
            </div>
            <span className="text-2xl font-bold text-white bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">
              SHARK TV
            </span>
          </div>
          <div className="hidden md:flex space-x-6">
            <a href="#pricing" className="text-gray-300 hover:text-white transition-all hover:scale-105 relative group">
              Planos
              <span className="absolute -bottom-1 left-0 w-0 h-0.5 bg-gradient-to-r from-blue-400 to-purple-400 group-hover:w-full transition-all"></span>
            </a>
            <a
              href="#features"
              className="text-gray-300 hover:text-white transition-all hover:scale-105 relative group"
            >
              Recursos
              <span className="absolute -bottom-1 left-0 w-0 h-0.5 bg-gradient-to-r from-blue-400 to-purple-400 group-hover:w-full transition-all"></span>
            </a>
            <a href="#contact" className="text-gray-300 hover:text-white transition-all hover:scale-105 relative group">
              Contato
              <span className="absolute -bottom-1 left-0 w-0 h-0.5 bg-gradient-to-r from-blue-400 to-purple-400 group-hover:w-full transition-all"></span>
            </a>
          </div>
        </nav>
      </header>

      {/* Hero Section */}
      <section className="container mx-auto px-4 py-20 text-center relative z-10">
        <div className="max-w-4xl mx-auto">
          <div className="animate-bounce mb-6">
            <Badge className="mb-4 bg-gradient-to-r from-green-500 to-emerald-500 hover:from-green-600 hover:to-emerald-600 text-white border-0 px-6 py-2 text-sm font-semibold shadow-lg shadow-green-500/25">
              🎉 Teste Grátis de 3 Horas Disponível
            </Badge>
          </div>

          <h1 className="text-5xl md:text-8xl font-black text-white mb-8 leading-tight">
            <span className="inline-block animate-pulse">Entretenimento</span>
            <br />
            <span className="text-transparent bg-clip-text bg-gradient-to-r from-blue-400 via-purple-400 to-pink-400 animate-gradient-x">
              Ilimitado
            </span>
          </h1>

          <p className="text-xl md:text-2xl text-gray-300 mb-12 max-w-3xl mx-auto leading-relaxed">
            🚀 Acesse <span className="text-yellow-400 font-bold">milhares de canais</span> em HD/4K, filmes, séries e
            esportes ao vivo.
            <br />
            Qualidade premium com <span className="text-green-400 font-bold">estabilidade garantida</span>.
          </p>

          {/* Stats */}
          <div className="grid grid-cols-2 md:grid-cols-4 gap-6 mb-12">
            <div className="bg-white/10 backdrop-blur-sm rounded-2xl p-4 border border-white/20 hover:bg-white/20 transition-all hover:scale-105">
              <div className="text-2xl font-bold text-blue-400">10K+</div>
              <div className="text-sm text-gray-300">Canais</div>
            </div>
            <div className="bg-white/10 backdrop-blur-sm rounded-2xl p-4 border border-white/20 hover:bg-white/20 transition-all hover:scale-105">
              <div className="text-2xl font-bold text-green-400">99.9%</div>
              <div className="text-sm text-gray-300">Uptime</div>
            </div>
            <div className="bg-white/10 backdrop-blur-sm rounded-2xl p-4 border border-white/20 hover:bg-white/20 transition-all hover:scale-105">
              <div className="text-2xl font-bold text-purple-400">4K</div>
              <div className="text-sm text-gray-300">Qualidade</div>
            </div>
            <div className="bg-white/10 backdrop-blur-sm rounded-2xl p-4 border border-white/20 hover:bg-white/20 transition-all hover:scale-105">
              <div className="text-2xl font-bold text-yellow-400">24/7</div>
              <div className="text-sm text-gray-300">Suporte</div>
            </div>
          </div>

          <div className="flex flex-col sm:flex-row gap-6 justify-center">
            <Button
              size="lg"
              className="bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-700 hover:to-pink-700 text-white px-10 py-4 text-lg font-semibold rounded-2xl shadow-2xl shadow-purple-500/25 hover:shadow-purple-500/40 transition-all hover:scale-105 border-0 group"
              onClick={() => window.open("http://wa.me/5519971672016", "_blank")}
            >
              <Play className="mr-3 h-6 w-6 group-hover:animate-pulse" />
              Teste Grátis 3h
              <div className="absolute inset-0 bg-gradient-to-r from-purple-600 to-pink-600 rounded-2xl blur-lg opacity-0 group-hover:opacity-30 transition-opacity -z-10"></div>
            </Button>
            <Button
              size="lg"
              variant="outline"
              className="border-2 border-purple-400 text-purple-400 hover:bg-purple-400 hover:text-white px-10 py-4 text-lg font-semibold rounded-2xl bg-transparent backdrop-blur-sm hover:shadow-2xl hover:shadow-purple-500/25 transition-all hover:scale-105 group"
              onClick={() => window.open("http://wa.me/5519971672016", "_blank")}
            >
              <Zap className="mr-3 h-6 w-6 group-hover:animate-bounce" />
              Ver Planos
            </Button>
          </div>
        </div>
      </section>

      {/* Features Section */}
      <section id="features" className="container mx-auto px-4 py-20 relative z-10">
        <div className="text-center mb-16">
          <h2 className="text-4xl md:text-6xl font-bold text-white mb-6 bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">
            Por que escolher SHARK TV?
          </h2>
          <p className="text-xl text-gray-300 max-w-3xl mx-auto">
            🎯 Oferecemos a melhor experiência em streaming com tecnologia de ponta
          </p>
        </div>

        <div className="grid md:grid-cols-3 gap-8">
          <Card className="bg-gradient-to-br from-slate-800/50 to-slate-900/50 border-slate-700/50 backdrop-blur-sm hover:bg-gradient-to-br hover:from-slate-700/50 hover:to-slate-800/50 transition-all hover:scale-105 hover:shadow-2xl hover:shadow-blue-500/10 group">
            <CardHeader>
              <div className="relative">
                <Shield className="h-16 w-16 text-blue-400 mb-4 group-hover:animate-pulse" />
                <div className="absolute inset-0 bg-blue-400 rounded-full blur-xl opacity-0 group-hover:opacity-20 transition-opacity"></div>
              </div>
              <CardTitle className="text-white text-xl group-hover:text-blue-400 transition-colors">
                🛡️ Estabilidade Garantida
              </CardTitle>
            </CardHeader>
            <CardContent>
              <p className="text-gray-300 group-hover:text-white transition-colors">
                Servidores premium com <span className="text-green-400 font-bold">99.9% de uptime</span>. Sem
                travamentos ou interrupções.
              </p>
            </CardContent>
          </Card>

          <Card className="bg-gradient-to-br from-slate-800/50 to-slate-900/50 border-slate-700/50 backdrop-blur-sm hover:bg-gradient-to-br hover:from-slate-700/50 hover:to-slate-800/50 transition-all hover:scale-105 hover:shadow-2xl hover:shadow-purple-500/10 group">
            <CardHeader>
              <div className="relative">
                <Zap className="h-16 w-16 text-purple-400 mb-4 group-hover:animate-bounce" />
                <div className="absolute inset-0 bg-purple-400 rounded-full blur-xl opacity-0 group-hover:opacity-20 transition-opacity"></div>
              </div>
              <CardTitle className="text-white text-xl group-hover:text-purple-400 transition-colors">
                ⚡ Qualidade 4K/HD
              </CardTitle>
            </CardHeader>
            <CardContent>
              <p className="text-gray-300 group-hover:text-white transition-colors">
                Transmissão em <span className="text-purple-400 font-bold">alta definição</span> com qualidade de imagem
                superior.
              </p>
            </CardContent>
          </Card>

          <Card className="bg-gradient-to-br from-slate-800/50 to-slate-900/50 border-slate-700/50 backdrop-blur-sm hover:bg-gradient-to-br hover:from-slate-700/50 hover:to-slate-800/50 transition-all hover:scale-105 hover:shadow-2xl hover:shadow-pink-500/10 group">
            <CardHeader>
              <div className="relative">
                <Globe className="h-16 w-16 text-pink-400 mb-4 group-hover:animate-spin" />
                <div className="absolute inset-0 bg-pink-400 rounded-full blur-xl opacity-0 group-hover:opacity-20 transition-opacity"></div>
              </div>
              <CardTitle className="text-white text-xl group-hover:text-pink-400 transition-colors">
                🌍 Canais Globais
              </CardTitle>
            </CardHeader>
            <CardContent>
              <p className="text-gray-300 group-hover:text-white transition-colors">
                Mais de <span className="text-yellow-400 font-bold">10.000 canais</span> do Brasil e do mundo. Esportes,
                filmes, séries e muito mais.
              </p>
            </CardContent>
          </Card>
        </div>
      </section>

      {/* Movies Banner Section */}
      <section className="container mx-auto px-4 py-20 relative z-10">
        <div className="text-center mb-16">
          <h2 className="text-4xl md:text-6xl font-bold text-white mb-6 bg-gradient-to-r from-yellow-400 to-orange-400 bg-clip-text text-transparent">
            🎬 Filmes em Destaque
          </h2>
          <p className="text-xl text-gray-300">Os maiores sucessos do cinema na palma da sua mão</p>
        </div>

        <div className="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-7 gap-6 mb-12">
          {[
            { src: "/images/f1-poster.webp", alt: "F1 - Filme" },
            { src: "/images/zombies4-poster.webp", alt: "Zombies 4 - Filme" },
            { src: "/images/superman-poster.webp", alt: "Superman - Filme" },
            { src: "/images/ballerina-poster.webp", alt: "Ballerina - Filme" },
            { src: "/images/jurassic-poster.webp", alt: "Jurassic World - Filme" },
            { src: "/images/chefes-poster.webp", alt: "Chefes de Estado - Filme" },
            { src: "/images/megan-poster.webp", alt: "Megan 2.0 - Filme" },
          ].map((movie, index) => (
            <div key={index} className="relative group cursor-pointer">
              <div className="relative overflow-hidden rounded-2xl">
                <img
                  src={movie.src || "/placeholder.svg"}
                  alt={movie.alt}
                  className="w-full h-64 object-cover transition-all duration-500 group-hover:scale-110"
                />
                <div className="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-all duration-300"></div>
                <div className="absolute inset-0 bg-black/50 opacity-0 group-hover:opacity-100 transition-all duration-300 rounded-2xl flex items-center justify-center">
                  <div className="bg-white/20 backdrop-blur-sm rounded-full p-4 group-hover:scale-110 transition-transform">
                    <Play className="h-8 w-8 text-white" />
                  </div>
                </div>
              </div>
              <div className="absolute -inset-1 bg-gradient-to-r from-purple-500 to-pink-500 rounded-2xl blur opacity-0 group-hover:opacity-30 transition-opacity -z-10"></div>
            </div>
          ))}
        </div>

        <div className="text-center">
          <Button
            size="lg"
            className="bg-gradient-to-r from-yellow-500 to-orange-500 hover:from-yellow-600 hover:to-orange-600 text-white px-10 py-4 text-lg font-semibold rounded-2xl shadow-2xl shadow-yellow-500/25 hover:shadow-yellow-500/40 transition-all hover:scale-105 border-0 group"
            onClick={() => window.open("http://wa.me/5519971672016", "_blank")}
          >
            <Star className="mr-3 h-6 w-6 group-hover:animate-spin" />
            Ver Catálogo Completo
          </Button>
        </div>
      </section>

      {/* Channels Section */}
      <section className="container mx-auto px-4 py-20 relative z-10">
        <div className="bg-gradient-to-r from-slate-800/30 to-slate-900/30 backdrop-blur-sm rounded-3xl p-8 border border-white/10">
          <div className="text-center mb-16">
            <h2 className="text-4xl md:text-6xl font-bold text-white mb-6 bg-gradient-to-r from-green-400 to-blue-400 bg-clip-text text-transparent">
              📺 Canais Disponíveis
            </h2>
            <p className="text-xl text-gray-300">Mais de 10.000 canais do Brasil e do mundo</p>
          </div>

          <div className="grid grid-cols-3 md:grid-cols-6 lg:grid-cols-8 gap-4 mb-12">
            {[
              "GLOBO",
              "SBT",
              "RECORD",
              "BAND",
              "ESPN",
              "FOX",
              "HBO",
              "NETFLIX",
              "DISNEY",
              "CARTOON",
              "DISCOVERY",
              "HISTORY",
              "NATGEO",
              "COMEDY",
              "PREMIERE",
              "SPORTV",
            ].map((channel, index) => (
              <div
                key={index}
                className="bg-gradient-to-br from-slate-700/50 to-slate-800/50 backdrop-blur-sm p-4 rounded-xl flex items-center justify-center h-20 hover:bg-gradient-to-br hover:from-slate-600/50 hover:to-slate-700/50 transition-all hover:scale-105 hover:shadow-lg border border-white/10 group cursor-pointer"
              >
                <span className="text-white font-bold text-sm text-center group-hover:text-blue-400 transition-colors">
                  {channel}
                </span>
              </div>
            ))}
          </div>

          <div className="grid md:grid-cols-3 gap-8 mb-12">
            {[
              {
                icon: Tv,
                title: "📺 Canais Nacionais",
                description: "Todos os canais abertos e fechados do Brasil",
                items: [
                  "• Globo, SBT, Record, Band",
                  "• GloboNews, CNN Brasil",
                  "• Multishow, GNT, Canal Brasil",
                  "• E muito mais...",
                ],
                color: "blue",
              },
              {
                icon: Globe,
                title: "🌍 Canais Internacionais",
                description: "Os melhores canais do mundo todo",
                items: [
                  "• HBO, Fox, Universal",
                  "• Discovery, History, NatGeo",
                  "• CNN, BBC, France 24",
                  "• E muito mais...",
                ],
                color: "purple",
              },
              {
                icon: Zap,
                title: "⚽ Esportes",
                description: "Todos os jogos e campeonatos",
                items: ["• Premiere, SporTV", "• ESPN, Fox Sports", "• Combate, BandSports", "• E muito mais..."],
                color: "green",
              },
            ].map((category, index) => (
              <Card
                key={index}
                className="bg-gradient-to-br from-slate-800/50 to-slate-900/50 border-slate-700/50 backdrop-blur-sm hover:bg-gradient-to-br hover:from-slate-700/50 hover:to-slate-800/50 transition-all hover:scale-105 hover:shadow-2xl group"
              >
                <CardHeader>
                  <CardTitle className="text-white flex items-center group-hover:text-blue-400 transition-colors">
                    <category.icon className="mr-3 h-6 w-6 text-purple-400 group-hover:animate-pulse" />
                    {category.title}
                  </CardTitle>
                </CardHeader>
                <CardContent>
                  <p className="text-gray-300 mb-4 group-hover:text-white transition-colors">{category.description}</p>
                  <ul className="text-sm text-gray-400 space-y-2 group-hover:text-gray-300 transition-colors">
                    {category.items.map((item, itemIndex) => (
                      <li key={itemIndex}>{item}</li>
                    ))}
                  </ul>
                </CardContent>
              </Card>
            ))}
          </div>

          <div className="text-center">
            <Button
              size="lg"
              className="bg-gradient-to-r from-green-500 to-blue-500 hover:from-green-600 hover:to-blue-600 text-white px-10 py-4 text-lg font-semibold rounded-2xl shadow-2xl shadow-green-500/25 hover:shadow-green-500/40 transition-all hover:scale-105 border-0 group"
              onClick={() => window.open("http://wa.me/5519971672016", "_blank")}
            >
              <Users className="mr-3 h-6 w-6 group-hover:animate-bounce" />
              Ver Lista Completa de Canais
            </Button>
          </div>
        </div>
      </section>

      {/* Pricing Section */}
      <section id="pricing" className="container mx-auto px-4 py-20 relative z-10">
        <div className="text-center mb-16">
          <h2 className="text-4xl md:text-6xl font-bold text-white mb-6 bg-gradient-to-r from-green-400 to-blue-400 bg-clip-text text-transparent">
            💰 Escolha seu Plano
          </h2>
          <p className="text-xl text-gray-300">Planos flexíveis para todas as necessidades</p>
        </div>

        <div className="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
          {/* Teste Grátis */}
          <Card className="bg-gradient-to-br from-slate-800/50 to-slate-900/50 border-slate-700/50 backdrop-blur-sm relative hover:scale-105 transition-all hover:shadow-2xl hover:shadow-green-500/20 group">
            <div className="absolute -inset-1 bg-gradient-to-r from-green-500 to-emerald-500 rounded-2xl blur opacity-0 group-hover:opacity-30 transition-opacity"></div>
            <div className="relative bg-gradient-to-br from-slate-800/90 to-slate-900/90 rounded-2xl">
              <CardHeader>
                <Badge className="w-fit bg-gradient-to-r from-green-500 to-emerald-500 text-white border-0 mb-2">
                  🎁 Grátis
                </Badge>
                <CardTitle className="text-white text-3xl group-hover:text-green-400 transition-colors">
                  Teste
                </CardTitle>
                <CardDescription className="text-gray-300 group-hover:text-white transition-colors">
                  Experimente por 3 horas
                </CardDescription>
              </CardHeader>
              <CardContent>
                <div className="text-5xl font-bold text-white mb-6 group-hover:text-green-400 transition-colors">
                  R$ 0<span className="text-lg text-gray-400">/3h</span>
                </div>
                <ul className="space-y-3">
                  {[
                    "Acesso completo por 3 horas",
                    "Todos os canais disponíveis",
                    "Qualidade HD/4K",
                    "Suporte técnico",
                  ].map((feature, index) => (
                    <li
                      key={index}
                      className="flex items-center text-gray-300 group-hover:text-white transition-colors"
                    >
                      <Check className="h-5 w-5 text-green-400 mr-3 group-hover:animate-pulse" />
                      {feature}
                    </li>
                  ))}
                </ul>
              </CardContent>
              <CardFooter>
                <Button
                  className="w-full bg-gradient-to-r from-green-500 to-emerald-500 hover:from-green-600 hover:to-emerald-600 text-white py-3 rounded-xl font-semibold shadow-lg hover:shadow-xl transition-all"
                  onClick={() => window.open("http://wa.me/5519971672016", "_blank")}
                >
                  <Play className="mr-2 h-5 w-5" />
                  Começar Teste
                </Button>
              </CardFooter>
            </div>
          </Card>

          {/* Plano Mensal */}
          <Card className="bg-gradient-to-br from-slate-800/50 to-slate-900/50 border-purple-500/50 backdrop-blur-sm relative hover:scale-105 transition-all hover:shadow-2xl hover:shadow-purple-500/20 group">
            <div className="absolute -inset-1 bg-gradient-to-r from-purple-500 to-pink-500 rounded-2xl blur opacity-30 group-hover:opacity-50 transition-opacity"></div>
            <div className="relative bg-gradient-to-br from-slate-800/90 to-slate-900/90 rounded-2xl">
              <CardHeader>
                <Badge className="w-fit bg-gradient-to-r from-purple-500 to-pink-500 text-white border-0 mb-2">
                  🔥 Popular
                </Badge>
                <CardTitle className="text-white text-3xl group-hover:text-purple-400 transition-colors">
                  Mensal
                </CardTitle>
                <CardDescription className="text-gray-300 group-hover:text-white transition-colors">
                  Flexibilidade total
                </CardDescription>
              </CardHeader>
              <CardContent>
                <div className="text-5xl font-bold text-white mb-6 group-hover:text-purple-400 transition-colors">
                  R$ 30<span className="text-lg text-gray-400">/mês</span>
                </div>
                <ul className="space-y-3">
                  {[
                    "+10.000 canais HD/4K",
                    "Filmes e séries ilimitados",
                    "Esportes ao vivo",
                    "Suporte 24/7",
                    "Múltiplos dispositivos",
                  ].map((feature, index) => (
                    <li
                      key={index}
                      className="flex items-center text-gray-300 group-hover:text-white transition-colors"
                    >
                      <Check className="h-5 w-5 text-green-400 mr-3 group-hover:animate-pulse" />
                      {feature}
                    </li>
                  ))}
                </ul>
              </CardContent>
              <CardFooter>
                <Button
                  className="w-full bg-gradient-to-r from-purple-500 to-pink-500 hover:from-purple-600 hover:to-pink-600 text-white py-3 rounded-xl font-semibold shadow-lg hover:shadow-xl transition-all"
                  onClick={() => window.open("http://wa.me/5519971672016", "_blank")}
                >
                  <Zap className="mr-2 h-5 w-5" />
                  Assinar Agora
                </Button>
              </CardFooter>
            </div>
          </Card>

          {/* Plano Trimestral */}
          <Card className="bg-gradient-to-br from-slate-800/50 to-slate-900/50 border-yellow-500/50 backdrop-blur-sm relative hover:scale-105 transition-all hover:shadow-2xl hover:shadow-yellow-500/20 group">
            <div className="absolute -top-4 left-1/2 transform -translate-x-1/2 z-10">
              <Badge className="bg-gradient-to-r from-yellow-500 to-orange-500 text-white px-4 py-2 text-sm font-bold shadow-lg">
                ⭐ Melhor Oferta
              </Badge>
            </div>
            <div className="absolute -inset-1 bg-gradient-to-r from-yellow-500 to-orange-500 rounded-2xl blur opacity-30 group-hover:opacity-50 transition-opacity"></div>
            <div className="relative bg-gradient-to-br from-slate-800/90 to-slate-900/90 rounded-2xl pt-8">
              <CardHeader>
                <CardTitle className="text-white text-3xl group-hover:text-yellow-400 transition-colors">
                  Trimestral
                </CardTitle>
                <CardDescription className="text-gray-300 group-hover:text-white transition-colors">
                  Economize mais de 30%
                </CardDescription>
              </CardHeader>
              <CardContent>
                <div className="text-5xl font-bold text-white mb-2 group-hover:text-yellow-400 transition-colors">
                  R$ 80<span className="text-lg text-gray-400">/3 meses</span>
                </div>
                <p className="text-sm text-green-400 mb-6 font-semibold">💰 Economia de R$ 10 vs mensal</p>
                <ul className="space-y-3">
                  {[
                    "+10.000 canais HD/4K",
                    "Filmes e séries ilimitados",
                    "Esportes ao vivo",
                    "Suporte prioritário 24/7",
                    "Múltiplos dispositivos",
                    "Garantia de reembolso",
                  ].map((feature, index) => (
                    <li
                      key={index}
                      className="flex items-center text-gray-300 group-hover:text-white transition-colors"
                    >
                      <Check className="h-5 w-5 text-green-400 mr-3 group-hover:animate-pulse" />
                      {feature}
                    </li>
                  ))}
                </ul>
              </CardContent>
              <CardFooter>
                <Button
                  className="w-full bg-gradient-to-r from-yellow-500 to-orange-500 hover:from-yellow-600 hover:to-orange-600 text-white py-3 rounded-xl font-semibold shadow-lg hover:shadow-xl transition-all"
                  onClick={() => window.open("http://wa.me/5519971672016", "_blank")}
                >
                  <Award className="mr-2 h-5 w-5" />
                  Assinar Trimestral
                </Button>
              </CardFooter>
            </div>
          </Card>
        </div>
      </section>

      {/* Contact Section */}
      <section id="contact" className="container mx-auto px-4 py-20 relative z-10">
        <div className="max-w-2xl mx-auto">
          <div className="text-center mb-12">
            <h2 className="text-4xl md:text-6xl font-bold text-white mb-6 bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">
              📞 Entre em Contato
            </h2>
            <p className="text-xl text-gray-300">Tem dúvidas? Nossa equipe está pronta para ajudar!</p>
          </div>

          <Card className="bg-gradient-to-br from-slate-800/50 to-slate-900/50 border-slate-700/50 backdrop-blur-sm hover:shadow-2xl hover:shadow-blue-500/10 transition-all group">
            <div className="absolute -inset-1 bg-gradient-to-r from-blue-500 to-purple-500 rounded-2xl blur opacity-0 group-hover:opacity-20 transition-opacity"></div>
            <div className="relative bg-gradient-to-br from-slate-800/90 to-slate-900/90 rounded-2xl">
              <CardHeader>
                <CardTitle className="text-white text-2xl group-hover:text-blue-400 transition-colors">
                  💬 Solicitar Informações
                </CardTitle>
                <CardDescription className="text-gray-300 group-hover:text-white transition-colors">
                  Preencha o formulário e entraremos em contato via WhatsApp
                </CardDescription>
              </CardHeader>
              <form onSubmit={handleSubmit}>
                <CardContent className="space-y-6">
                  <div className="grid grid-cols-2 gap-4">
                    <div>
                      <Label htmlFor="name" className="text-gray-300 font-semibold">
                        Nome *
                      </Label>
                      <Input
                        id="name"
                        name="name"
                        placeholder="Seu nome completo"
                        className="bg-slate-700/50 border-slate-600/50 text-white backdrop-blur-sm focus:border-blue-400 focus:ring-blue-400 rounded-xl"
                        value={formData.name}
                        onChange={handleInputChange}
                        required
                      />
                    </div>
                    <div>
                      <Label htmlFor="phone" className="text-gray-300 font-semibold">
                        WhatsApp *
                      </Label>
                      <Input
                        id="phone"
                        name="phone"
                        placeholder="(11) 99999-9999"
                        className="bg-slate-700/50 border-slate-600/50 text-white backdrop-blur-sm focus:border-blue-400 focus:ring-blue-400 rounded-xl"
                        value={formData.phone}
                        onChange={handleInputChange}
                        required
                      />
                    </div>
                  </div>
                  <div>
                    <Label htmlFor="email" className="text-gray-300 font-semibold">
                      Email *
                    </Label>
                    <Input
                      id="email"
                      name="email"
                      type="email"
                      placeholder="seu@email.com"
                      className="bg-slate-700/50 border-slate-600/50 text-white backdrop-blur-sm focus:border-blue-400 focus:ring-blue-400 rounded-xl"
                      value={formData.email}
                      onChange={handleInputChange}
                      required
                    />
                  </div>
                  <div>
                    <Label htmlFor="plan" className="text-gray-300 font-semibold">
                      Plano de Interesse
                    </Label>
                    <select
                      id="plan"
                      name="plan"
                      className="w-full p-3 bg-slate-700/50 border border-slate-600/50 rounded-xl text-white backdrop-blur-sm focus:border-blue-400 focus:ring-blue-400"
                      value={formData.plan}
                      onChange={handleInputChange}
                    >
                      <option>Teste Grátis 3h</option>
                      <option>Plano Mensal - R$ 30</option>
                      <option>Plano Trimestral - R$ 80</option>
                    </select>
                  </div>
                  <div>
                    <Label htmlFor="message" className="text-gray-300 font-semibold">
                      Mensagem (opcional)
                    </Label>
                    <Textarea
                      id="message"
                      name="message"
                      placeholder="Conte-nos como podemos ajudar..."
                      className="bg-slate-700/50 border-slate-600/50 text-white backdrop-blur-sm focus:border-blue-400 focus:ring-blue-400 rounded-xl"
                      value={formData.message}
                      onChange={handleInputChange}
                    />
                  </div>

                  {submitStatus === "success" && (
                    <div className="bg-green-600/20 border border-green-600/50 rounded-xl p-4 backdrop-blur-sm">
                      <p className="text-green-400 text-sm font-semibold">
                        ✅ Formulário enviado! Redirecionando para o WhatsApp...
                      </p>
                    </div>
                  )}

                  {submitStatus === "error" && (
                    <div className="bg-red-600/20 border border-red-600/50 rounded-xl p-4 backdrop-blur-sm">
                      <p className="text-red-400 text-sm font-semibold">
                        ❌ Erro ao enviar. Tente novamente ou entre em contato diretamente.
                      </p>
                    </div>
                  )}
                </CardContent>
                <CardFooter>
                  <Button
                    type="submit"
                    className="w-full bg-gradient-to-r from-blue-500 to-purple-500 hover:from-blue-600 hover:to-purple-600 disabled:opacity-50 text-white py-3 rounded-xl font-semibold shadow-lg hover:shadow-xl transition-all group"
                    disabled={!isFormValid || isSubmitting}
                  >
                    {isSubmitting ? (
                      <>
                        <Loader2 className="mr-2 h-5 w-5 animate-spin" />
                        Enviando...
                      </>
                    ) : (
                      <>
                        <Send className="mr-2 h-5 w-5 group-hover:animate-pulse" />
                        Enviar para WhatsApp
                      </>
                    )}
                  </Button>
                </CardFooter>
              </form>
            </div>
          </Card>
        </div>
      </section>

      {/* Footer */}
      <footer className="bg-gradient-to-r from-slate-900/90 to-slate-800/90 border-t border-slate-700/50 backdrop-blur-sm relative z-10">
        <div className="container mx-auto px-4 py-8">
          <div className="flex flex-col md:flex-row justify-between items-center">
            <div className="flex items-center space-x-3 mb-4 md:mb-0 group">
              <div className="relative">
                <img
                  src="/images/sharktv-logo.png"
                  alt="Shark TV Logo"
                  className="h-10 w-10 object-contain transition-transform group-hover:scale-110 group-hover:rotate-12"
                />
                <div className="absolute inset-0 bg-gradient-to-r from-blue-500 to-purple-500 rounded-full blur-lg opacity-0 group-hover:opacity-30 transition-opacity"></div>
              </div>
              <span className="text-xl font-bold text-white bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">
                SHARK TV
              </span>
            </div>
            <div className="text-gray-400 text-sm">© 2024 SHARK TV. Todos os direitos reservados.</div>
          </div>
        </div>
      </footer>

      <style jsx>{`
        @keyframes gradient-x {
          0%, 100% {
            background-size: 200% 200%;
            background-position: left center;
          }
          50% {
            background-size: 200% 200%;
            background-position: right center;
          }
        }
        .animate-gradient-x {
          animation: gradient-x 3s ease infinite;
        }
      `}</style>
    </div>
  )
}


import React, { useEffect, useState } from 'react';
import { Mail, Phone, Code, User, FileText, Menu, X, ChevronDown, ArrowRight, Sparkles, MapPin, Calendar, GraduationCap } from 'lucide-react';
import { Button } from '@/components/ui/button';
import { Card, CardContent } from '@/components/ui/card';
import { Badge } from '@/components/ui/badge';
import DownloadButton from '@/components/DownloadButton';

const Index = () => {
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [activeSection, setActiveSection] = useState('home');

  useEffect(() => {
    const handleScroll = () => {
      const sections = ['home', 'about', 'services', 'portfolio', 'contact'];
      const scrollPosition = window.scrollY + 100;
      
      for (const section of sections) {
        const element = document.getElementById(section);
        if (element) {
          const offsetTop = element.offsetTop;
          const offsetHeight = element.offsetHeight;
          
          if (scrollPosition >= offsetTop && scrollPosition < offsetTop + offsetHeight) {
            setActiveSection(section);
            break;
          }
        }
      }
    };

    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const scrollToSection = (sectionId: string) => {
    const element = document.getElementById(sectionId);
    if (element) {
      element.scrollIntoView({
        behavior: 'smooth'
      });
    }
    setIsMenuOpen(false);
  };

  const skills = ['Full-Stack Development', 'HTML & CSS', 'JavaScript', 'Java', 'Responsive Design', 'Accessible Code', 'Database Design', 'API Development'];
  
  const services = [
    {
      title: 'Frontend Development',
      description: 'Creating responsive, interactive user interfaces with modern technologies and best practices.',
      icon: <Code className="w-8 h-8" />,
      features: ['React & Modern JS', 'Responsive Design', 'Performance Optimization', 'Accessibility']
    },
    {
      title: 'Backend Development', 
      description: 'Building robust server-side applications and APIs with Java and modern frameworks.',
      icon: <FileText className="w-8 h-8" />,
      features: ['Java Development', 'API Design', 'Database Management', 'Security Implementation']
    },
    {
      title: 'Full-Stack Solutions',
      description: 'End-to-end web development combining frontend and backend expertise for complete solutions.',
      icon: <User className="w-8 h-8" />,
      features: ['Complete Solutions', 'System Architecture', 'DevOps Integration', 'Scalable Applications']
    }
  ];

  return (
    <div className="min-h-screen bg-gradient-to-br from-violet-100 via-slate-50 to-purple-100 relative overflow-hidden">
      {/* Enhanced Animated Background Elements */}
      <div className="fixed inset-0 pointer-events-none">
        <div className="absolute top-20 left-10 w-32 h-32 bg-gradient-to-br from-violet-300/20 to-purple-300/20 rounded-full animate-float blur-sm"></div>
        <div className="absolute top-40 right-20 w-24 h-24 bg-gradient-to-br from-purple-300/20 to-violet-400/20 rounded-full animate-float blur-sm" style={{ animationDelay: '2s' }}></div>
        <div className="absolute bottom-40 left-1/4 w-40 h-40 bg-gradient-to-br from-violet-200/20 to-purple-200/20 rounded-full animate-float blur-sm" style={{ animationDelay: '4s' }}></div>
        <div className="absolute top-1/3 right-1/3 w-20 h-20 bg-gradient-to-r from-violet-400/30 to-purple-400/30 rotate-45 animate-rotate-slow rounded-lg"></div>
        <div className="absolute bottom-20 right-10 w-28 h-28 bg-gradient-to-r from-purple-400/30 to-violet-500/30 rotate-45 animate-rotate-slow rounded-lg" style={{ animationDelay: '10s' }}></div>
        
        {/* New modern grid pattern */}
        <div className="absolute inset-0 opacity-[0.02]">
          <div className="h-full w-full bg-[linear-gradient(to_right,#8b5cf6_1px,transparent_1px),linear-gradient(to_bottom,#8b5cf6_1px,transparent_1px)] bg-[size:4rem_4rem]"></div>
        </div>
      </div>

      {/* Navigation */}
      <nav className="fixed top-0 left-0 right-0 bg-white/80 backdrop-blur-md z-50 border-b border-violet-200/30">
        <div className="container mx-auto px-6 py-4">
          <div className="flex justify-between items-center">
            <div className="text-2xl font-bold text-primary">Vengatraman G</div>
            
            {/* Desktop Navigation */}
            <div className="hidden md:flex space-x-8">
              {['home', 'about', 'services', 'portfolio', 'contact'].map((section) => (
                <button
                  key={section}
                  onClick={() => scrollToSection(section)}
                  className={`capitalize font-medium transition-colors duration-300 hover:text-primary ${
                    activeSection === section ? 'text-primary' : 'text-gray-600'
                  }`}
                >
                  {section}
                </button>
              ))}
            </div>

            {/* Mobile Menu Button */}
            <button
              className="md:hidden"
              onClick={() => setIsMenuOpen(!isMenuOpen)}
            >
              {isMenuOpen ? <X className="w-6 h-6" /> : <Menu className="w-6 h-6" />}
            </button>
          </div>

          {/* Mobile Navigation */}
          {isMenuOpen && (
            <div className="md:hidden mt-4 pb-4">
              {['home', 'about', 'services', 'portfolio', 'contact'].map((section) => (
                <button
                  key={section}
                  onClick={() => scrollToSection(section)}
                  className="block w-full text-left py-2 capitalize font-medium text-gray-600 hover:text-primary transition-colors"
                >
                  {section}
                </button>
              ))}
            </div>
          )}
        </div>
      </nav>

      {/* Enhanced Hero Section */}
      <section id="home" className="min-h-screen flex items-center justify-center pt-20 relative">
        <div className="container mx-auto px-6">
          <div className="max-w-5xl mx-auto text-center">
            {/* Status Badge */}
            <div className="inline-flex items-center gap-2 bg-white/80 backdrop-blur-sm border border-primary/20 rounded-full px-4 py-2 mb-8 animate-fade-in">
              <div className="w-2 h-2 bg-green-500 rounded-full animate-pulse"></div>
              <span className="text-sm font-medium text-gray-700">Available for opportunities</span>
            </div>

            {/* Enhanced Profile Section with Real Photo */}
            <div className="relative inline-block mb-12 animate-scale-in">
              <div className="relative">
                {/* Glowing border effect */}
                <div className="absolute inset-0 bg-gradient-to-r from-primary via-secondary to-accent rounded-full p-[3px] animate-rotate-slow">
                  <div className="w-full h-full bg-white rounded-full"></div>
                </div>
                
                {/* Profile container with actual photo */}
                <div className="relative w-56 h-56 mx-auto rounded-full bg-gradient-to-br from-primary/5 to-secondary/5 p-1">
                  <div className="w-full h-full rounded-full bg-white flex items-center justify-center shadow-2xl overflow-hidden">
                    <img 
                      src="https://i.postimg.cc/jjZVx6YS/Whats-App-Image-vengat.jpg" 
                      alt="Vengatraman G - Full-Stack Web Developer" 
                      className="w-full h-full object-cover rounded-full"
                      onError={(e) => {
                        // Fallback to icon if image fails to load
                        e.currentTarget.style.display = 'none';
                        const fallbackDiv = e.currentTarget.nextElementSibling as HTMLElement;
                        if (fallbackDiv) {
                          fallbackDiv.style.display = 'flex';
                        }
                      }}
                    />
                    <div className="w-full h-full rounded-full bg-white hidden items-center justify-center">
                      <User className="w-28 h-28 text-primary" />
                    </div>
                  </div>
                </div>
                
                {/* Floating accent elements */}
                <div className="absolute -top-6 -right-6 w-12 h-12 bg-gradient-to-br from-accent to-secondary rounded-full animate-float flex items-center justify-center">
                  <Sparkles className="w-6 h-6 text-white" />
                </div>
                <div className="absolute -bottom-4 -left-4 w-8 h-8 bg-gradient-to-br from-primary to-accent rounded-full animate-float" style={{ animationDelay: '1s' }}></div>
              </div>
            </div>
            
            {/* Enhanced Typography */}
            <div className="space-y-6 animate-slide-in-up">
              <h1 className="text-6xl md:text-8xl font-bold text-gray-900 leading-tight">
                Hi, I'm{' '}
                <span className="bg-gradient-to-r from-primary via-secondary to-accent bg-clip-text text-transparent animate-pulse">
                  Vengatraman
                </span>
              </h1>
              
              <div className="relative">
                <p className="text-2xl md:text-3xl text-gray-600 font-light max-w-4xl mx-auto leading-relaxed">
                  Future Full-Stack Web Developer passionate about creating{' '}
                  <span className="font-semibold text-primary">innovative digital solutions</span>
                </p>
                
                {/* Underline accent */}
                <div className="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-32 h-1 bg-gradient-to-r from-primary to-secondary rounded-full mt-2"></div>
              </div>
            </div>
            
            {/* Enhanced Action Buttons */}
            <div className="flex flex-col sm:flex-row gap-6 justify-center mt-12 animate-slide-in-up" style={{ animationDelay: '0.4s' }}>
              <Button
                size="lg"
                className="group bg-gradient-to-r from-primary to-primary/90 hover:from-primary/90 hover:to-primary text-white px-10 py-4 text-lg font-semibold rounded-full shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1"
                onClick={() => scrollToSection('portfolio')}
              >
                Explore My Work
                <ArrowRight className="w-5 h-5 ml-2 group-hover:translate-x-1 transition-transform duration-300" />
              </Button>
              
              <Button
                variant="outline"
                size="lg"
                className="group border-2 border-primary/30 bg-white/80 backdrop-blur-sm text-primary hover:bg-primary hover:text-white px-10 py-4 text-lg font-semibold rounded-full shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1"
                onClick={() => scrollToSection('contact')}
              >
                Get In Touch
                <Mail className="w-5 h-5 ml-2 group-hover:scale-110 transition-transform duration-300" />
              </Button>
            </div>

            {/* Enhanced Bio with Stats */}
            <div className="mt-16 animate-slide-in-up" style={{ animationDelay: '0.6s' }}>
              <div className="bg-white/60 backdrop-blur-sm rounded-2xl p-8 max-w-4xl mx-auto border border-white/20 shadow-xl">
                <p className="text-lg text-gray-700 leading-relaxed mb-6">
                  Computer Science Engineering graduate with{' '}
                  <span className="font-bold text-primary">CGPA 8.2</span>, specializing in{' '}
                  <span className="font-semibold text-secondary">HTML, CSS, Java, and JavaScript</span>.
                  <br />
                  Currently advancing my full-stack development expertise.
                </p>
                
                {/* Stats Grid */}
                <div className="grid grid-cols-2 md:grid-cols-4 gap-6 mt-8">
                  <div className="text-center">
                    <div className="text-2xl font-bold text-primary">8.2</div>
                    <div className="text-sm text-gray-600">CGPA</div>
                  </div>
                  <div className="text-center">
                    <div className="text-2xl font-bold text-secondary">2026</div>
                    <div className="text-sm text-gray-600">Graduate</div>
                  </div>
                  <div className="text-center">
                    <div className="text-2xl font-bold text-accent">Full-Stack</div>
                    <div className="text-sm text-gray-600">Focus</div>
                  </div>
                  <div className="text-center">
                    <div className="text-2xl font-bold text-primary">CSE</div>
                    <div className="text-sm text-gray-600">Degree</div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          {/* Enhanced Scroll Indicator */}
          <div className="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
            <div className="flex flex-col items-center gap-2">
              <div className="w-6 h-10 border-2 border-gray-400 rounded-full flex justify-center">
                <div className="w-1 h-3 bg-gray-400 rounded-full mt-2 animate-pulse"></div>
              </div>
              <ChevronDown className="w-4 h-4 text-gray-400" />
            </div>
          </div>
        </div>
      </section>

      {/* Enhanced About Section */}
      <section id="about" className="py-24 bg-gradient-to-br from-white via-violet-50/30 to-purple-50/30 relative">
        {/* Subtle background pattern */}
        <div className="absolute inset-0 opacity-[0.015]">
          <div className="h-full w-full bg-[radial-gradient(circle_at_50%_50%,#8b5cf6_1px,transparent_1px)] bg-[size:32px_32px]"></div>
        </div>
        
        <div className="container mx-auto px-6 relative">
          <div className="max-w-6xl mx-auto">
            {/* Section Header */}
            <div className="text-center mb-20">
              <div className="inline-flex items-center gap-2 bg-primary/5 rounded-full px-4 py-2 mb-6">
                <User className="w-4 h-4 text-primary" />
                <span className="text-sm font-medium text-primary">Get to know me</span>
              </div>
              <h2 className="text-5xl font-bold text-gray-900 mb-6">About Me</h2>
              <div className="w-24 h-1 bg-gradient-to-r from-primary to-secondary mx-auto rounded-full"></div>
            </div>
            
            <div className="grid lg:grid-cols-2 gap-16 items-start">
              {/* Left Column - Bio & Education */}
              <div className="space-y-8">
                <div className="bg-gradient-to-br from-white to-gray-50/50 p-8 rounded-2xl border border-gray-100 shadow-lg hover:shadow-xl transition-all duration-300">
                  <h3 className="text-2xl font-bold text-gray-900 mb-6 flex items-center gap-3">
                    <div className="w-8 h-8 bg-primary/10 rounded-lg flex items-center justify-center">
                      <Sparkles className="w-4 h-4 text-primary" />
                    </div>
                    My Journey
                  </h3>
                  <p className="text-lg text-gray-600 leading-relaxed mb-6">
                    I'm a Computer Science Engineering graduate with a strong academic foundation (CGPA 8.2) 
                    and a passion for full-stack web development. My journey in technology is driven by 
                    curiosity and a commitment to creating accessible, high-performance web solutions.
                  </p>
                  <p className="text-gray-600 leading-relaxed">
                    Currently advancing my expertise in modern web technologies, I'm excited to contribute 
                    to innovative projects that make a real impact.
                  </p>
                </div>

                {/* Education Card */}
                <div className="bg-gradient-to-br from-primary/5 to-secondary/5 p-8 rounded-2xl border border-primary/10 shadow-lg">
                  <h3 className="text-xl font-bold text-gray-900 mb-6 flex items-center gap-3">
                    <div className="w-8 h-8 bg-primary/20 rounded-lg flex items-center justify-center">
                      <GraduationCap className="w-4 h-4 text-primary" />
                    </div>
                    Education
                  </h3>
                  <div className="space-y-4">
                    <div className="flex items-center justify-between">
                      <div>
                        <p className="font-semibold text-gray-900">Computer Science Engineering</p>
                        <p className="text-gray-600">Bachelor's Degree</p>
                      </div>
                      <Badge variant="secondary" className="bg-primary/10 text-primary">
                        CGPA 8.2/10
                      </Badge>
                    </div>
                    <div className="flex items-center gap-2 text-gray-600">
                      <Calendar className="w-4 h-4" />
                      <span>Graduated 2026</span>
                    </div>
                  </div>
                </div>
              </div>

              {/* Right Column - Skills */}
              <div className="space-y-8">
                <div className="bg-gradient-to-br from-white to-gray-50/50 p-8 rounded-2xl border border-gray-100 shadow-lg">
                  <h3 className="text-2xl font-bold text-gray-900 mb-8 flex items-center gap-3">
                    <div className="w-8 h-8 bg-secondary/10 rounded-lg flex items-center justify-center">
                      <Code className="w-4 h-4 text-secondary" />
                    </div>
                    Technical Skills
                  </h3>
                  <div className="grid grid-cols-2 gap-4">
                    {skills.map((skill, index) => (
                      <div
                        key={skill}
                        className="group bg-gradient-to-br from-gray-50 to-white p-4 rounded-xl border border-gray-100 hover:border-primary/20 hover:shadow-md transition-all duration-300 hover:-translate-y-1"
                        style={{ animationDelay: ${index * 0.1}s }}
                      >
                        <div className="flex items-center gap-3">
                          <div className="w-2 h-2 bg-gradient-to-r from-primary to-secondary rounded-full group-hover:scale-125 transition-transform duration-300"></div>
                          <span className="text-sm font-medium text-gray-800 group-hover:text-primary transition-colors duration-300">
                            {skill}
                          </span>
                        </div>
                      </div>
                    ))}
                  </div>
                </div>

                {/* Quick Stats */}
                <div className="grid grid-cols-2 gap-4">
                  <div className="bg-gradient-to-br from-primary/5 to-primary/10 p-6 rounded-xl text-center border border-primary/10">
                    <div className="text-3xl font-bold text-primary mb-2">8.2</div>
                    <div className="text-sm text-gray-600">Academic CGPA</div>
                  </div>
                  <div className="bg-gradient-to-br from-secondary/5 to-secondary/10 p-6 rounded-xl text-center border border-secondary/10">
                    <div className="text-3xl font-bold text-secondary mb-2">2024</div>
                    <div className="text-sm text-gray-600">Graduate</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Enhanced Services Section */}
      <section id="services" className="py-24 bg-gradient-to-br from-violet-50/50 to-purple-50/50 relative">
        <div className="absolute inset-0 opacity-[0.02]">
          <div className="h-full w-full bg-[linear-gradient(45deg,#8b5cf6_1px,transparent_1px),linear-gradient(-45deg,#a855f7_1px,transparent_1px)] bg-[size:60px_60px]"></div>
        </div>

        <div className="container mx-auto px-6 relative">
          <div className="max-w-7xl mx-auto">
            {/* Section Header */}
            <div className="text-center mb-20">
              <div className="inline-flex items-center gap-2 bg-secondary/5 rounded-full px-4 py-2 mb-6">
                <FileText className="w-4 h-4 text-secondary" />
                <span className="text-sm font-medium text-secondary">What I offer</span>
              </div>
              <h2 className="text-5xl font-bold text-gray-900 mb-6">Services</h2>
              <p className="text-xl text-gray-600 max-w-3xl mx-auto leading-relaxed">
                I offer comprehensive web development services, focusing on creating responsive, 
                accessible, and performant applications that deliver exceptional user experiences.
              </p>
              <div className="w-24 h-1 bg-gradient-to-r from-secondary to-accent mx-auto rounded-full mt-6"></div>
            </div>
            
            <div className="grid lg:grid-cols-3 gap-8">
              {services.map((service, index) => (
                <Card
                  key={service.title}
                  className="group hover:shadow-2xl transition-all duration-500 hover:-translate-y-4 border-0 bg-white overflow-hidden relative"
                  style={{ animationDelay: ${index * 0.2}s }}
                >
                  {/* Gradient overlay */}
                  <div className="absolute inset-0 bg-gradient-to-br from-primary/5 via-transparent to-secondary/5 opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
                  
                  <CardContent className="p-8 relative z-10">
                    {/* Icon */}
                    <div className="mb-8">
                      <div className="w-16 h-16 bg-gradient-to-br from-primary/10 to-secondary/10 rounded-2xl flex items-center justify-center group-hover:scale-110 transition-transform duration-300 mb-4">
                        <div className="text-primary group-hover:text-secondary transition-colors duration-300">
                          {service.icon}
                        </div>
                      </div>
                      <h3 className="text-2xl font-bold text-gray-900 group-hover:text-primary transition-colors duration-300">
                        {service.title}
                      </h3>
                    </div>

                    {/* Description */}
                    <p className="text-gray-600 leading-relaxed mb-6 group-hover:text-gray-700 transition-colors duration-300">
                      {service.description}
                    </p>

                    {/* Features */}
                    <div className="space-y-3">
                      {service.features.map((feature, featureIndex) => (
                        <div key={feature} className="flex items-center gap-3">
                          <div className="w-1.5 h-1.5 bg-gradient-to-r from-primary to-secondary rounded-full"></div>
                          <span className="text-sm text-gray-600 group-hover:text-gray-700 transition-colors duration-300">
                            {feature}
                          </span>
                        </div>
                      ))}
                    </div>

                    {/* Hover indicator */}
                    <div className="mt-6 flex items-center gap-2 text-primary opacity-0 group-hover:opacity-100 transition-all duration-300 transform translate-y-2 group-hover:translate-y-0">
                      <span className="text-sm font-medium">Learn more</span>
                      <ArrowRight className="w-4 h-4" />
                    </div>
                  </CardContent>
                </Card>
              ))}
            </div>
          </div>
        </div>
      </section>

      {/* Enhanced Portfolio Section */}
      <section id="portfolio" className="py-24 bg-gradient-to-br from-white via-violet-50/20 to-white relative">
        <div className="absolute inset-0 opacity-[0.01]">
          <div className="h-full w-full bg-[radial-gradient(circle_at_25%_25%,#8b5cf6_2px,transparent_2px)] bg-[size:48px_48px]"></div>
        </div>

        <div className="container mx-auto px-6 relative">
          <div className="max-w-6xl mx-auto text-center">
            {/* Section Header */}
            <div className="mb-20">
              <div className="inline-flex items-center gap-2 bg-accent/5 rounded-full px-4 py-2 mb-6">
                <Code className="w-4 h-4 text-accent" />
                <span className="text-sm font-medium text-accent">My work</span>
              </div>
              <h2 className="text-5xl font-bold text-gray-900 mb-6">Portfolio</h2>
              <p className="text-xl text-gray-600 mb-8 max-w-3xl mx-auto">
                Exciting projects coming soon! I'm currently working on innovative full-stack applications 
                that showcase my growing expertise in modern web development.
              </p>
              <div className="w-24 h-1 bg-gradient-to-r from-accent to-primary mx-auto rounded-full"></div>
            </div>
            
            {/* Coming Soon Card */}
            <Card className="bg-gradient-to-br from-white via-gray-50/50 to-accent/5 border-2 border-dashed border-gray-200 hover:border-accent/30 transition-all duration-500 hover:shadow-2xl group overflow-hidden relative">
              {/* Animated background */}
              <div className="absolute inset-0 bg-gradient-to-r from-primary/5 via-secondary/5 to-accent/5 opacity-0 group-hover:opacity-100 transition-opacity duration-700"></div>
              
              <CardContent className="p-16 relative z-10">
                {/* Icon with animation */}
                <div className="relative mb-8">
                  <div className="w-32 h-32 mx-auto bg-white rounded-full flex items-center justify-center shadow-2xl group-hover:shadow-accent/20 transition-all duration-500 group-hover:scale-110">
                    <Code className="w-16 h-16 text-accent group-hover:text-primary transition-colors duration-500" />
                  </div>
                  
                  {/* Floating elements */}
                  <div className="absolute -top-4 -right-4 w-8 h-8 bg-gradient-to-br from-primary to-secondary rounded-full animate-float opacity-70"></div>
                  <div className="absolute -bottom-2 -left-6 w-6 h-6 bg-gradient-to-br from-secondary to-accent rounded-full animate-float opacity-70" style={{ animationDelay: '1s' }}></div>
                </div>

                <h3 className="text-3xl font-bold text-gray-900 mb-6 group-hover:text-primary transition-colors duration-300">
                  Projects In Development
                </h3>
                
                <p className="text-lg text-gray-600 mb-8 max-w-2xl mx-auto leading-relaxed group-hover:text-gray-700 transition-colors duration-300">
                  I'm actively building full-stack applications that demonstrate responsive design, 
                  accessibility best practices, and modern development techniques. Stay tuned for exciting updates!
                </p>

                {/* Tech Stack */}
                <div className="flex flex-wrap justify-center gap-3 mb-8">
                  {['React', 'Java', 'JavaScript', 'Responsive Design', 'Full-Stack', 'Modern UI'].map((tech, index) => (
                    <Badge
                      key={tech}
                      variant="secondary"
                      className="bg-gradient-to-r from-gray-100 to-gray-50 text-gray-700 hover:from-primary/10 hover:to-secondary/10 hover:text-primary transition-all duration-300 px-4 py-2 text-sm font-medium"
                      style={{ animationDelay: ${index * 0.1}s }}
                    >
                      {tech}
                    </Badge>
                  ))}
                </div>

                {/* Progress indicator */}
                <div className="max-w-md mx-auto">
                  <div className="flex items-center justify-between text-sm text-gray-500 mb-2">
                    <span>In Progress</span>
                    <span>Coming Soon</span>
                  </div>
                  <div className="w-full bg-gray-200 rounded-full h-2 overflow-hidden">
                    <div className="h-full bg-gradient-to-r from-primary via-secondary to-accent rounded-full animate-pulse" style={{ width: '75%' }}></div>
                  </div>
                </div>
              </CardContent>
            </Card>
          </div>
        </div>
      </section>

      {/* Enhanced Contact Section */}
      <section id="contact" className="py-24 bg-gradient-to-br from-violet-100/30 via-white to-purple-100/30 relative">
        <div className="absolute inset-0 opacity-[0.02]">
          <div className="h-full w-full bg-[conic-gradient(from_0deg_at_50%_50%,#8b5cf6_0deg,#a855f7_120deg,#9333ea_240deg,#8b5cf6_360deg)] bg-[size:400px_400px]"></div>
        </div>

        <div className="container mx-auto px-6 relative">
          <div className="max-w-5xl mx-auto">
            {/* Section Header */}
            <div className="text-center mb-20">
              <div className="inline-flex items-center gap-2 bg-primary/5 rounded-full px-4 py-2 mb-6">
                <Mail className="w-4 h-4 text-primary" />
                <span className="text-sm font-medium text-primary">Let's connect</span>
              </div>
              <h2 className="text-5xl font-bold text-gray-900 mb-6">Get In Touch</h2>
              <p className="text-xl text-gray-600 mb-8 max-w-3xl mx-auto">
                Ready to discuss your next project? I'd love to hear from you and explore how we can work together 
                to bring your ideas to life.
              </p>
              <div className="w-24 h-1 bg-gradient-to-r from-primary to-secondary mx-auto rounded-full"></div>
            </div>
            
            {/* Contact Cards */}
            <div className="grid md:grid-cols-2 gap-8 mb-16">
              <Card className="group hover:shadow-2xl transition-all duration-500 hover:-translate-y-2 border-0 bg-white overflow-hidden relative">
                <div className="absolute inset-0 bg-gradient-to-br from-primary/5 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
                <CardContent className="p-10 text-center relative z-10">
                  <div className="w-20 h-20 mx-auto mb-6 bg-gradient-to-br from-primary/10 to-primary/20 rounded-2xl flex items-center justify-center group-hover:scale-110 transition-transform duration-300">
                    <Mail className="w-10 h-10 text-primary" />
                  </div>
                  <h3 className="text-2xl font-bold text-gray-900 mb-4 group-hover:text-primary transition-colors duration-300">Email</h3>
                  <p className="text-gray-600 text-lg group-hover:text-gray-700 transition-colors duration-300">vengatraman.g@email.com</p>
                  <div className="mt-4 flex items-center justify-center gap-2 text-primary opacity-0 group-hover:opacity-100 transition-all duration-300">
                    <span className="text-sm font-medium">Send message</span>
                    <ArrowRight className="w-4 h-4" />
                  </div>
                </CardContent>
              </Card>
              
              <Card className="group hover:shadow-2xl transition-all duration-500 hover:-translate-y-2 border-0 bg-white overflow-hidden relative">
                <div className="absolute inset-0 bg-gradient-to-br from-secondary/5 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
                <CardContent className="p-10 text-center relative z-10">
                  <div className="w-20 h-20 mx-auto mb-6 bg-gradient-to-br from-secondary/10 to-secondary/20 rounded-2xl flex items-center justify-center group-hover:scale-110 transition-transform duration-300">
                    <Phone className="w-10 h-10 text-secondary" />
                  </div>
                  <h3 className="text-2xl font-bold text-gray-900 mb-4 group-hover:text-secondary transition-colors duration-300">Phone</h3>
                  <p className="text-gray-600 text-lg group-hover:text-gray-700 transition-colors duration-300">+91 XXXXX XXXXX</p>
                  <div className="mt-4 flex items-center justify-center gap-2 text-secondary opacity-0 group-hover:opacity-100 transition-all duration-300">
                    <span className="text-sm font-medium">Call now</span>
                    <ArrowRight className="w-4 h-4" />
                  </div>
                </CardContent>
              </Card>
            </div>
            
            {/* CTA Section */}
            <div className="text-center bg-white/80 backdrop-blur-sm rounded-3xl p-12 border border-white/20 shadow-xl">
              <h3 className="text-2xl font-bold text-gray-900 mb-4">Ready to Start Your Project?</h3>
              <p className="text-gray-600 mb-8 max-w-2xl mx-auto">
                Let's discuss your vision and create something amazing together. Download my resume or get in touch directly.
              </p>
              
              <div className="flex flex-col sm:flex-row gap-4 justify-center">
                <DownloadButton
                  size="lg"
                  className="bg-gradient-to-r from-primary to-primary/90 hover:from-primary/90 hover:to-primary text-white px-8 py-4 text-lg font-semibold rounded-full shadow-lg hover:shadow-xl transition-all duration-300 hover:-translate-y-1"
                />
                
                <Button
                  variant="outline"
                  size="lg"
                  className="group border-2 border-secondary/30 bg-white/80 backdrop-blur-sm text-secondary hover:bg-secondary hover:text-white px-8 py-4 text-lg font-semibold rounded-full shadow-lg hover:shadow-xl transition-all duration-300 hover:-translate-y-1"
                  onClick={() => scrollToSection('home')}
                >
                  <ArrowRight className="w-5 h-5 mr-2 group-hover:translate-x-1 transition-transform duration-300" />
                  Back to Top
                </Button>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Enhanced Footer */}
      <footer className="bg-gradient-to-r from-violet-900 via-purple-900 to-violet-900 text-white py-16 relative overflow-hidden">
        {/* Background pattern */}
        <div className="absolute inset-0 opacity-5">
          <div className="h-full w-full bg-[linear-gradient(45deg,#ffffff_1px,transparent_1px)] bg-[size:32px_32px]"></div>
        </div>

        <div className="container mx-auto px-6 text-center relative z-10">
          <div className="mb-12">
            <h3 className="text-3xl font-bold mb-4 bg-gradient-to-r from-primary to-secondary bg-clip-text text-transparent">
              Vengatraman G
            </h3>
            <p className="text-gray-300 max-w-md mx-auto text-lg leading-relaxed">
              Full-Stack Web Developer passionate about creating innovative digital solutions 
              that make a difference.
            </p>
          </div>

          {/* Quick Links */}
          <div className="flex flex-wrap justify-center gap-8 mb-12">
            {['home', 'about', 'services', 'portfolio', 'contact'].map((section) => (
              <button
                key={section}
                onClick={() => scrollToSection(section)}
                className="capitalize text-gray-300 hover:text-white transition-colors duration-300 hover:scale-105 transform font-medium"
              >
                {section}
              </button>
            ))}
          </div>
          
          <div className="border-t border-gray-700 pt-8">
            <p className="text-gray-400 flex items-center justify-center gap-2">
              © 2024 Vengatraman G. All rights reserved. 
              <span className="text-gray-500">•</span>
              Built with 
              <span className="text-primary font-medium">React</span> 
              & 
              <span className="text-secondary font-medium">Tailwind CSS</span>
              <Sparkles className="w-4 h-4 text-accent ml-1" />
            </p>
          </div>
        </div>
      </footer>
    </div>
  );
};

export default Index;

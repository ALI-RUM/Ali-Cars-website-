import React, { useState, useEffect } from "react";
import { Link } from "react-router-dom";
import { createPageUrl } from "../utils";
import { Car } from "../entities/Car";
import { ArrowRight, Star, Shield, Award, Users } from "lucide-react";
import { Button } from "../components/ui/button";
import { Card, CardContent } from "../components/ui/card";

import FeaturedCars from "../components/home/FeaturedCars";
import StatsSection from "../components/home/StatsSection";

export default function Home() {
  const [featuredCars, setFeaturedCars] = useState([]);
  const [isLoading, setIsLoading] = useState(true);

  useEffect(() => {
    loadFeaturedCars();
  }, []);

  const loadFeaturedCars = async () => {
    try {
      const cars = await Car.filter({ is_featured: true, is_sold: false }, "-created_date", 6);
      setFeaturedCars(cars);
    } catch (error) {
      console.error("Error loading featured cars:", error);
    } finally {
      setIsLoading(false);
    }
  };

  return (
    <div className="bg-white">
      {/* Hero Section with Video */}
      <section className="relative text-white overflow-hidden">
        <video
          className="absolute inset-0 w-full h-full object-cover"
          src="https://www.example.com/your-video.mp4"
          autoPlay
          loop
          muted
          playsInline
        />
        <div className="absolute inset-0 bg-black opacity-40"></div>
        <div className="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-24 lg:py-32">
          <div className="grid lg:grid-cols-2 gap-12 items-center">
            <div>
              <h1 className="text-4xl lg:text-6xl font-bold leading-tight mb-6">
                Vind uw perfecte
                <span className="block text-blue-300">Tweedehands Auto</span>
              </h1>
              <p className="text-xl text-blue-100 mb-8 leading-relaxed">
                Ontdek kwaliteitsvoertuigen die grondig zijn geïnspecteerd en gecertificeerd. Uw droomauto wacht op u bij Ali-Cars.
              </p>
              <div className="flex flex-col sm:flex-row gap-4">
                <Link to={createPageUrl("Cars")}>
                  <Button size="lg" className="bg-white text-blue-900 hover:bg-gray-100 px-8 py-3">
                    Bekijk Onze Auto's
                    <ArrowRight className="ml-2 w-5 h-5" />
                  </Button>
                </Link>
                <Link to={createPageUrl("Contact")}>
                  <Button size="lg" variant="outline" className="border-white text-white hover:bg-white hover:text-blue-900 px-8 py-3">
                    Contacteer Ons
                  </Button>
                </Link>
              </div>
            </div>
            <div className="relative">
              <div className="absolute inset-0 rounded-3xl overflow-hidden">
                <video
                  className="w-full h-full object-cover"
                  src="https://www.example.com/car-animation.mp4"
                  autoPlay
                  loop
                  muted
                  playsInline
                />
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Why Choose Us Section */}
      <section className="py-20 bg-gray-50">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="text-center mb-16">
            <h2 className="text-3xl lg:text-4xl font-bold text-gray-900 mb-4">Waarom kiezen voor Ali-Cars?</h2>
            <p className="text-xl text-gray-600 max-w-3xl mx-auto">
              Wij streven ernaar u de beste aankoopervaring te bieden door kwaliteit, transparantie en uitzonderlijke service.
            </p>
          </div>
          <div className="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
            <Card className="text-center border-none shadow-lg hover:shadow-xl transition-shadow duration-300">
              <CardContent className="p-8">
                <div className="w-16 h-16 bg-blue-100 rounded-full flex items-center justify-center mx-auto mb-6">
                  <Shield className="w-8 h-8 text-blue-600" />
                </div>
                <h3 className="text-xl font-semibold mb-4">Kwaliteit Gegarandeerd</h3>
                <p className="text-gray-600">Elk voertuig ondergaat een grondige inspectie om betrouwbaarheid en veiligheid te garanderen.</p>
              </CardContent>
            </Card>

            <Card className="text-center border-none shadow-lg

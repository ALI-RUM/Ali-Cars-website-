# Ali-Cars-website-


import React from "react";
import { Button } from "@/components/ui/button";
import { Label } from "@/components/ui/label";
import {
  Select,
  SelectContent,
  SelectItem,
  SelectTrigger,
  SelectValue,
} from "@/components/ui/select";
import { X } from "lucide-react";


export default function CarFilters({ filters, onFilterChange, onClearFilters, uniqueMakes }) {
  const handleFilterChange = (key, value) => {
    onFilterChange({
      ...filters,
      [key]: value
    });
  };


  const hasActiveFilters = Object.values(filters).some(v => v);


  return (
    <div className="space-y-6">
      <div className="flex items-center justify-between">
        <h3 className="text-lg font-semibold text-gray-900">Filters</h3>
        {hasActiveFilters && (
          <Button
            variant="ghost"
            size="sm"
            onClick={onClearFilters}
            className="text-blue-600 hover:text-blue-700"
          >
            <X className="w-4 h-4 mr-1" />
            Wissen
          </Button>
        )}
      </div>


      <div className="space-y-4">
        <div>
          <Label className="text-sm font-medium text-gray-700">Merk</Label>
          <Select value={filters.make} onValueChange={(value) => handleFilterChange('make', value)}>
            <SelectTrigger className="mt-1">
              <SelectValue placeholder="Alle merken" />
            </SelectTrigger>
            <SelectContent>
              <SelectItem value={null}>Alle merken</SelectItem>
              {uniqueMakes.map((make) => (
                <SelectItem key={make} value={make}>
                  {make}
                </SelectItem>
              ))}
            </SelectContent>
          </Select>
        </div>


        <div>
          <Label className="text-sm font-medium text-gray-700">Prijsklasse</Label>
          <Select value={filters.priceRange} onValueChange={(value) => handleFilterChange('priceRange', value)}>
            <SelectTrigger className="mt-1">
              <SelectValue placeholder="Elke prijs" />
            </SelectTrigger>
            <SelectContent>
              <SelectItem value={null}>Elke prijs</SelectItem>
              <SelectItem value="under-10k">Onder €10.000</SelectItem>
              <SelectItem value="10k-20k">€10.000 - €20.000</SelectItem>
              <SelectItem value="20k-30k">€20.000 - €30.000</SelectItem>
              <SelectItem value="over-30k">Boven €30.000</SelectItem>
            </SelectContent>
          </Select>
        </div>


        <div>
          <Label className="text-sm font-medium text-gray-700">Brandstoftype</Label>
          <Select value={filters.fuelType} onValueChange={(value) => handleFilterChange('fuelType', value)}>
            <SelectTrigger className="mt-1">
              <SelectValue placeholder="Elk brandstoftype" />
            </SelectTrigger>
            <SelectContent>
              <SelectItem value={null}>Elk brandstoftype</SelectItem>
              <SelectItem value="Gasoline">Benzine</SelectItem>
              <SelectItem value="Diesel">Diesel</SelectItem>
              <SelectItem value="Hybrid">Hybride</SelectItem>
              <SelectItem value="Electric">Elektrisch</SelectItem>
            </SelectContent>
          </Select>
        </div>


        <div>
          <Label className="text-sm font-medium text-gray-700">Transmissie</Label>
          <Select value={filters.transmission} onValueChange={(value) => handleFilterChange('transmission', value)}>
            <SelectTrigger className="mt-1">
              <SelectValue placeholder="Elke transmissie" />
            </SelectTrigger>
            <SelectContent>
              <SelectItem value={null}>Elke transmissie</SelectItem>
              <SelectItem value="Manual">Handgeschakeld</SelectItem>
              <SelectItem value="Automatic">Automaat</SelectItem>
            </SelectContent>
          </Select>
        </div>


        <div>
          <Label className="text-sm font-medium text-gray-700">Carrosserietype</Label>
          <Select value={filters.bodyType} onValueChange={(value) => handleFilterChange('bodyType', value)}>
            <SelectTrigger className="mt-1">
              <SelectValue placeholder="Elk carrosserietype" />
            </SelectTrigger>
            <SelectContent>
              <SelectItem value={null}>Elk carrosserietype</SelectItem>
              <SelectItem value="Sedan">Sedan</SelectItem>
              <SelectItem value="SUV">SUV</SelectItem>
              <SelectItem value="Hatchback">Hatchback</SelectItem>
              <SelectItem value="Coupe">Coupé</SelectItem>
              <SelectItem value="Convertible">Cabriolet</SelectItem>
              <SelectItem value="Truck">Vrachtwagen</SelectItem>
              <SelectItem value="Van">Bestelwagen</SelectItem>
            </SelectContent>
          </Select>
        </div>


        <div>
          <Label className="text-sm font-medium text-gray-700">Staat</Label>
          <Select value={filters.condition} onValueChange={(value) => handleFilterChange('condition', value)}>
            <SelectTrigger className="mt-1">
              <SelectValue placeholder="Elke staat" />
            </SelectTrigger>
            <SelectContent>
              <SelectItem value={null}>Elke staat</SelectItem>
              <SelectItem value="Excellent">Uitstekend</SelectItem>
              <SelectItem value="Very Good">Zeer Goed</SelectItem>
              <SelectItem value="Good">Goed</SelectItem>
              <SelectItem value="Fair">Redelijk</SelectItem>
            </SelectContent>
          </Select>
        </div>
      </div>
    </div>
  );
}



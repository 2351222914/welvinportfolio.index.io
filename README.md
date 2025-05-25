
import { Trophy, Beaker } from "lucide-react";

export const Achievements = () => {
  const achievements = [
{
title: "Third Place in Product Pitching",
      description: "Recognized for innovative product presentation and business proposal skills in agribusiness competition.",
      icon: Trophy,
      color: "amber",
      year: "2025",
      image: "/lovable-uploads/df8c3ad2-3bc1-40bc-b523-1650bf888705.png"
    },
    {
    title: "Agricultural Research Project",
      description: "Conducted hands-on research in sustainable agriculture and food systems development.",
      icon: Beaker,
      color: "green",
      year: "2024",
      image: "/lovable-uploads/4e55cfdf-b724-44ad-9965-c0ef6b706fa9.png"
      }
  ];

  const getColorClasses = (color: string) => {
    const colors = {
      amber: "from-amber-400 to-amber-600 text-amber-600 bg-amber-100 border-amber-200",
      green: "from-green-400 to-green-600 text-green-600 bg-green-100 border-green-200"
    };
    return colors[color as keyof typeof colors];
  };

  return (
    <section id="achievements" className="py-20 bg-white">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-16 animate-fade-in">
          <h2 className="text-4xl sm:text-5xl font-bold text-gray-900 mb-4">
            My <span className="bg-gradient-to-r from-blue-600 to-indigo-600 bg-clip-text text-transparent">Achievements</span>
          </h2>
          <div className="w-24 h-1 bg-gradient-to-r from-blue-600 to-indigo-600 mx-auto rounded-full mb-6"></div>
          <p className="text-xl text-gray-600 max-w-3xl mx-auto">
            Recognition for excellence in academic and professional pursuits in agribusiness.
          </p>
        </div>

        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          {achievements.map((achievement, index) => {
            const colorClasses = getColorClasses(achievement.color);
            const [gradientClass, textClass, bgClass, borderClass] = colorClasses.split(' ');

            return (
              <div 
                key={index}
                className={`group bg-white rounded-2xl p-8 shadow-lg hover:shadow-2xl transition-all duration-500 transform hover:scale-105 animate-fade-in border-2 ${borderClass}`}
                style={{ animationDelay: `${index * 100}ms` }}
              >
                <div className="flex flex-col items-center text-center space-y-6">
                  {achievement.image && (
                    <div className="w-full h-48 rounded-xl overflow-hidden shadow-md mb-4">
                      <img 
                        src={achievement.image}
                        alt={achievement.title}
                        className="w-full h-full object-cover object-center"
                      />
                    </div>
                  )}

                  <div className={`p-4 rounded-2xl ${bgClass} group-hover:bg-gradient-to-r group-hover:${gradientClass} group-hover:text-white transition-all duration-300 relative`}>
                    <achievement.icon size={40} className={`${textClass} group-hover:text-white transition-colors duration-300`} />
                    <div className={`absolute -top-2 -right-2 ${achievement.color === 'amber' ? 'bg-amber-500' : 'bg-green-500'} text-white text-xs font-bold px-2 py-1 rounded-full`}>
                      {achievement.year}
                    </div>
                  </div>

                  <div className="space-y-3">
                    <h3 className="text-xl font-bold text-gray-900 group-hover:text-gray-800 transition-colors duration-300">
                      {achievement.title}
                    </h3>
                    
                    <p className="text-gray-600 leading-relaxed group-hover:text-gray-700 transition-colors duration-300">
                      {achievement.description}
                    </p>
                  </div>

                  <div className={`flex items-center space-x-2 ${achievement.color === 'amber' ? 'text-amber-600' : 'text-green-600'} font-semibold`}>
                    {achievement.color === 'amber' ? (
                      <>
                        <Trophy size={16} />
                        <span className="text-sm">3rd Place</span>
                      </>
                    ) : (
                      <>
                        <Beaker size={16} />
                        <span className="text-sm">Research</span>
                      </>
                    )}
                  </div>
                </div>
              </div>
            );
          })}
        </div>
      </div>
    </section>
  );
};

# CYPERSECURITYAPP
la comunidad CyberSecurity
import React, { useState } from 'react';

export default function CyberSecurityApp() {
  const [activeTab, setActiveTab] = useState('about');
  const [contributions, setContributions] = useState([]);
  const [newContribution, setNewContribution] = useState('');

  const handleTabClick = (tab: string) => {
    setActiveTab(tab);
  };

  const handleInputChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    setNewContribution(e.target.value);
  };

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    if (newContribution.trim() !== '') {
      setContributions([...contributions, newContribution]);
      setNewContribution('');
    }
  };

  return (
    <div className="bg-gray-100 min-h-screen py-8 px-4">
      <header className="bg-white shadow rounded-md p-4 mb-8">
        <h1 className="text-2xl font-semibold text-gray-800">CyberSecurity Community App</h1>
        <p className="text-gray-600">Committed to protecting information and fighting digital threats.</p>
      </header>

      <nav className="bg-white shadow rounded-md p-4 mb-8">
        <ul className="flex space-x-4">
          <li>
            <button
              className={`px-4 py-2 rounded-md ${
                activeTab === 'about'
                  ? 'bg-blue-500 text-white'
                  : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
              }`}
              onClick={() => handleTabClick('about')}
            >
              About
            </button>
          </li>
          <li>
            <button
              className={`px-4 py-2 rounded-md ${
                activeTab === 'contributions'
                  ? 'bg-blue-500 text-white'
                  : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
              }`}
              onClick={() => handleTabClick('contributions')}
            >
              My Contributions
            </button>
          </li>
          <li>
            <button
              className={`px-4 py-2 rounded-md ${
                activeTab === 'resources'
                  ? 'bg-blue-500 text-white'
                  : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
              }`}
              onClick={() => handleTabClick('resources')}
            >
              Resources
            </button>
          </li>
        </ul>
      </nav>

      <main className="bg-white shadow rounded-md p-4">
        {activeTab === 'about' && (
          <div>
            <h2 className="text-xl font-semibold text-gray-800 mb-4">About Me</h2>
            <p className="text-gray-700">
              My expertise lies in information security, forensic analysis, and cyberattack prevention. I am eager to
              contribute to identifying and mitigating risks, enhancing the community's integrity.
            </p>
            <p className="text-gray-700 mt-2">
              I am motivated to collaborate on investigations, share advanced strategies, and work together to maintain a
              secure cyberspace. I am committed to upholding professionalism, discretion, and ethical standards in this
              endeavor.
            </p>
            <div className="mt-4">
              <h3 className="text-lg font-semibold text-gray-800 mb-2">Skills</h3>
              <ul className="list-disc list-inside text-gray-700">
                <li>Security Information and Event Management (SIEM)</li>
                <li>Intrusion Detection and Prevention Systems (IDPS)</li>
                <li>Vulnerability Assessment and Penetration Testing</li>
                <li>Incident Response</li>
                <li>Network Security</li>
              </ul>
            </div>
          </div>
        )}

        {activeTab === 'contributions' && (
          <div>
            <h2 className="text-xl font-semibold text-gray-800 mb-4">My Contributions</h2>
            <form onSubmit={handleSubmit} className="mb-4">
              <input
                type="text"
                placeholder="Add a new contribution..."
                value={newContribution}
                onChange={handleInputChange}
                className="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
              />
              <button
                type="submit"
                className="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline mt-2"
              >
                Add
              </button>
            </form>
            <ul>
              {contributions.map((contribution, index) => (
                <li key={index} className="text-gray-700 py-2 border-b border-gray-200">
                  {contribution}
                </li>
              ))}
            </ul>
            {contributions.length === 0 && <p className="text-gray-500">No contributions yet.</p>}
          </div>
        )}

        {activeTab === 'resources' && (
          <div>
            <h2 className="text-xl font-semibold text-gray-800 mb-4">Resources</h2>
            <p className="text-gray-700">
              Here are some valuable cybersecurity resources:
            </p>
            <ul className="list-disc list-inside text-gray-700">
              <li>
                <a href="https://www.cisecurity.org/" target="_blank" rel="noopener noreferrer" className="text-blue-500 hover:underline">
                  Center for Internet Security (CIS)
                </a>
              </li>
              <li>
                <a href="https://www.nist.gov/cybersecurity" target="_blank" rel="noopener noreferrer" className="text-blue-500 hover:underline">
                  National Institute of Standards and Technology (NIST) Cybersecurity
                </a>
              </li>
              <li>
                <a href="https://www.sans.org/" target="_blank" rel="noopener noreferrer" className="text-blue-500 hover:underline">
                  SANS Institute
                </a>
              </li>
            </ul>
          </div>
        )}
      </main>
    </div>
  );
}

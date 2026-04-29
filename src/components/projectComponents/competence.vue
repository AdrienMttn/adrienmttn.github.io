<script lang="ts" setup>
const listCompetences: { [key: string]: any } = {
  "A" : {
    "title" : "Gérer le patrimoine informatique",
    "color" : "-green-500",
    "sousCompetences" : [
      "Recenser et identifier les ressources numériques",
      "Exploiter des référentiels, normes et standards adoptés par le prestataire informatique",
      "Mettre en place et vérifier les niveaux d’habilitation associés à un service",
      "Vérifier les conditions de la continuité d’un service informatique",
      "Gérer des sauvegardes",
      "Vérifier le respect des règles d’utilisation des ressources numériques"
    ]
  },
  "B" : {
    "title": "Répondre aux incidents et aux demandes d’assistance et d’évolution",
    "color" : "-blue-500",
    "sousCompetences" : [
      "Collecter, suivre et orienter des demandes",
      "Traiter des demandes concernant les services réseau et système, applicatifs",
      "Traiter des demandes concernant les applications"
    ]
  },
  "C" : {
    "title" : "Développer la présence en ligne de l’organisation",
    "color" : "-yellow-500",
    "sousCompetences" : [
      "Participer à la valorisation de l’image de l’organisation sur les médias numériques en tenant compte du cadre juridique et des enjeux économiques",
      "Référencer les services en ligne de l’organisation et mesurer leur visibilité",
      "Participer à l’évolution d’un site Web exploitant les données de l’organisation"
    ]
  },
  "D" : {
    "title" : "Travailler en mode projet",
    "color" : "-red-500",
    "sousCompetences" : [
      "Analyser les objectifs et les modalités d’organisation d’un projet",
      "Planifier les activités",
      "Évaluer les indicateurs de suivi d’un projet et analyser les écarts"
    ]
  },
  "E" : {
    "title" : "Mettre à disposition des utilisateurs un service informatique",
    "color" : "-purple-500",
    "sousCompetences" : [
      "Réaliser les tests d’intégration et d’acceptation d’un service",
      "Déployer un service",
      "Accompagner les utilisateurs dans la mise en place d’un service"
    ]
  },
  "F" : {
    "title" : "Organiser son développement professionnel",
    "color" : "-cyan-500",
    "sousCompetences" : [
      "Mettre en place son environnement d’apprentissage personnel",
      "Mettre en œuvre des outils et stratégies de veille informationnelle",
      "Gérer son identité professionnelle",
      "Développer son projet professionnel"
    ]
  }
}

const props = defineProps<{
  competence: string;
  sousCompetences: number;
}>();

const competenceData = `${listCompetences[props.competence].title} ( ${listCompetences[props.competence].sousCompetences[props.sousCompetences]} )`;
const color = listCompetences[props.competence].color;
</script>

<template>
  <div class="flex gap-2 items-center">
    <div :class="`border${color} text${color}`" class="flex gap-2 rounded-full border w-15 h-8 text-sm font-bold items-center justify-center">
      <p>{{ `${props.competence}.${sousCompetences}`}}</p>
    </div>
    <p class="text-sm">{{ competenceData }}</p>
  </div>
</template>
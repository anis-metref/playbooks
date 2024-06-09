### Mise à jour du système Debian en utilisant Ansible :

Le playbook Ansible update.yml met à jour les systèmes d'exploitation Debian et envoie une notification à Discord en cas de succès ou d'échec de la mise à jour :


Ce Playbook Ansible effectue les actions suivantes :

1.  **Mise à jour des paquets Debian** : Utilise le module `apt` pour mettre à jour les paquets Debian sur les systèmes cibles. Le résultat de cette tâche est enregistré dans la variable `apt_update_result`.
2.  **Notification à Discord en cas de succès** : Utilise le module `uri` pour envoyer une notification à Discord si la mise à jour des paquets Debian a réussi. La condition `when` vérifie si la variable `apt_update_result.changed` est vraie. Le contenu de la notification inclut le nom de l'hôte Ansible sur lequel la mise à jour a été effectuée. La réponse du serveur Discord est enregistrée dans la variable `discord_response_success`.
3.  **Notification à Discord en cas d'échec** : Utilise également le module `uri` pour envoyer une notification à Discord en cas d'échec de la mise à jour des paquets Debian. La condition `when` vérifie si la variable `apt_update_result.failed` est vraie. Le contenu de la notification indique qu'il y a eu un échec de mise à jour sur l'hôte Ansible concerné. La réponse du serveur Discord est enregistrée dans la variable `discord_response_failure`.
4.  **Affichage des réponses du serveur Discord** : Utilise le module `debug` pour afficher les réponses du serveur Discord en cas de succès ou d'échec. Cela permet de vérifier les réponses reçues.

N'oubliez pas de remplacer les valeurs `WEBHOOK_ID` et `TOKEN` dans les URL des webhooks Discord par les valeurs correspondantes de votre webhook Discord.

1. Installer `docker` sur le [site officiel ](https://www.docker.com/)
   
2. Vérifier que l'installation est correctement effectuée en les commandes suivante dans le terminal
   ```
   docker pull hello-world
   docker run hello-world
   ```

3. Télécharger l'image de `elasticsearch` avec la comamnde suivante: 
   ```
   docker pull elasticsearch:8.3.1
   ```

4. Enfin lancer le container avec la commande de configuration suivante (permet d'éviter les soucis d'authification auprès de l'API d'elasticsearch)
   ```
   docker run -d --name elasticsearch --net es_net -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e "xpack.security.enabled=false" -t docker.elastic.co/elasticsearch/elasticsearch:8.3.1
   ```

   Le container est visible est lançant la commande suivante: 
   ```
   docker ps
   ```

5. L'API `elasticsearch` est atteignable sur le port 9200, exemple:
    ```
    curl localhost:9200
    ```
    réponse: 
    ```JSON
    {
    "name" : "fab4bc38dc62",
    "cluster_name" : "docker-cluster",
    "cluster_uuid" : "x0kNa_OvQTeySVyW5l1HGg",
    "version" : {
      "number" : "8.3.1",
      "build_type" : "docker",
      "build_hash" : "b9a6b2867996ba92ceac66cb5bafc6db25e7910e",
      "build_date" : "2022-06-29T18:39:55.731992798Z",
      "build_snapshot" : false,
      "lucene_version" : "9.2.0",
      "minimum_wire_compatibility_version" : "7.17.0",
      "minimum_index_compatibility_version" : "7.0.0"
    },
    "tagline" : "You Know, for Search"
     }
   ```

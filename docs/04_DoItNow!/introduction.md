---
layout: default
title: 4.1 Introduction
parent: 4. DoItNow!
nav_order: 1
---

# 4.1 Projektumsetzung und Technologieeinsatz

## 4.1.1 Projektübersicht

### Einführung in das Projekt

Das Projekt «DOITNOW!» zielt darauf ab, eine minimalistische ToDo-Listen-Anwendung zu entwickeln, die es Benutzern ermöglicht, ihre Aufgaben effizient zu verwalten und abzuschließen. Viele vorhandene ToDo-Listen-Anwendungen sind überladen mit Funktionen, die nicht immer notwendig sind. Im Gegensatz dazu konzentriert sich «DOITNOW!» auf das Wesentliche, um eine intuitive und benutzerfreundliche Erfahrung zu bieten.

### Zielsetzung

Die Hauptziele des Projekts sind:
- **Minimalistische Benutzeroberfläche**: Eine einfache und intuitive Oberfläche, auf der Benutzer Aufgaben hinzufügen, bearbeiten und abhaken können.
- **Microservices-Architektur**: Flexibilität und Erweiterbarkeit durch eine modulare Architektur, bei der einzelne Komponenten der Anwendung unabhängig entwickelt und skaliert werden können.
- **Skalierbarkeit und Wartbarkeit**: Nutzung von Docker für die Containerisierung und AWS für das Hosting, um eine skalierbare und leicht wartbare Umgebung zu schaffen.
- **Trennung von Backend und Frontend**: Verwendung von Flask API für das Backend und HTTP-Templates für das Frontend, um eine klare Trennung der Logik zu gewährleisten.
- **Automatisierte CI/CD Pipeline**: Implementierung einer Continuous Integration und Continuous Deployment Pipeline mit GitLab, um den Entwicklungs- und Bereitstellungsprozess zu optimieren.

## 4.1.2 Microservices-Prinzip

### Was sind Microservices?

Microservices sind ein Architekturmuster, bei dem eine Anwendung aus einer Sammlung kleiner, unabhängiger Dienste besteht, die jeweils einen spezifischen Geschäftsprozess oder eine spezifische Funktion abdecken. Jeder Microservice ist autonom und kann unabhängig entwickelt, bereitgestellt und skaliert werden. Dies unterscheidet sich von monolithischen Architekturen, bei denen alle Funktionen in einer einzigen, zusammenhängenden Codebasis verwaltet werden.

### Funktionsweise der Microservices

In einer Microservices-Architektur ist jeder Dienst für einen klar definierten Teil der Geschäftslogik verantwortlich. Diese Dienste kommunizieren typischerweise über leichtgewichtige Protokolle wie HTTP/HTTPS oder Messaging-Systeme (z.B. RabbitMQ) und tauschen Daten oft in standardisierten Formaten wie JSON oder XML aus.

Ein typisches Beispiel für die Funktionsweise von Microservices kann wie folgt aussehen:

1. **Benutzerverwaltung**: Ein eigener Microservice kümmert sich um die Registrierung, Authentifizierung und Verwaltung von Benutzerdaten. Dieser Dienst speichert Benutzerinformationen und stellt APIs für die Interaktion mit diesen Daten bereit.
2. **Aufgabenverwaltung**: Ein weiterer Microservice verwaltet die Aufgaben des Benutzers. Er bietet Funktionen zum Erstellen, Bearbeiten, Löschen und Abrufen von Aufgaben. Dieser Dienst kann auch Benachrichtigungen oder Erinnerungen bereitstellen.
3. **Benachrichtigungsdienst**: Ein separater Dienst könnte Benachrichtigungen und E-Mails an Benutzer senden, z.B. Erinnerungen an fällige Aufgaben oder Willkommensnachrichten nach der Registrierung.
4. **Kommunikation**: Die Dienste kommunizieren über definierte APIs miteinander. Zum Beispiel könnte der Benutzerdienst Anfragen vom Aufgabenverwaltungsdienst erhalten, um sicherzustellen, dass der Benutzer authentifiziert ist, bevor Aufgabeninformationen bereitgestellt werden.

### Vorteile der Microservices-Architektur

- **Unabhängige Entwicklung und Deployment**: Entwicklerteams können an verschiedenen Diensten unabhängig voneinander arbeiten und diese bereitstellen, ohne dass Änderungen an einem Dienst den Betrieb anderer beeinflussen.
- **Skalierbarkeit**: Jeder Dienst kann unabhängig skaliert werden. Wenn z.B. der Benachrichtigungsdienst stark ausgelastet ist, kann er separat skaliert werden, ohne andere Teile der Anwendung zu beeinflussen.
- **Flexibilität bei der Technologieauswahl**: Verschiedene Microservices können mit unterschiedlichen Technologien und Programmiersprachen entwickelt werden, was die Flexibilität erhöht.
- **Erhöhte Ausfallsicherheit**: Da die Dienste unabhängig voneinander laufen, kann ein Fehler in einem Dienst isoliert werden, ohne die gesamte Anwendung zum Stillstand zu bringen.

### Anwendung der Microservices in diesem Projekt

In diesem Projekt zur Entwicklung einer ToDo-Listen-Anwendung werden die Microservices wie folgt eingesetzt:

1. **Backend-Architektur**:
   - **Benutzer-API**: Verwalten von Benutzerinformationen, Registrierungen und Authentifizierungen.
   - **Aufgaben-API**: Verwalten der Benutzeraufgaben, einschließlich der Funktionen zum Erstellen, Bearbeiten, Löschen und Abrufen von Aufgaben.
   
2. **Kommunikation zwischen Diensten**:
   - Die Dienste kommunizieren über RESTful APIs.
   
3. **Deployment und Management**:
   - Jeder Microservice wird in einem Docker-Container ausgeführt und auf AWS EC2-Instanzen bereitgestellt. Die Verwaltung und Orchestrierung dieser Container wird durch AWS-Dienste unterstützt, die eine einfache Skalierung und Wartung ermöglichen.

## 4.1.3 AWS (Amazon Web Services) und AWS Academy Lab

Die Anwendung wird auf AWS gehostet, einer führenden Cloud-Plattform, die uns eine robuste Infrastruktur bietet. Durch den Zugang zum AWS Academy Lab können wir praktische Erfahrungen mit AWS-Services wie EC2 (Elastic Compute Cloud), S3 (Simple Storage Service) und RDS (Relational Database Service) sammeln. Diese Dienste werden genutzt, um die Anwendung in einer sicheren und skalierbaren Cloud-Umgebung zu betreiben.

## 4.1.4 GitLab und CI/CD mit GitLab Pipelines

GitLab wird als zentrale Entwicklungsplattform verwendet. Die Entwicklung erfolgt in Git-Repositories, wo Entwickler gemeinsam an Code arbeiten und Änderungen verwalten können. Durch die Integration von GitLab Pipelines wird Continuous Integration (CI) und Continuous Deployment (CD) realisiert. Dies bedeutet, dass Änderungen automatisch getestet und bei erfolgreicher Prüfung automatisch in die Produktion überführt werden.

## 4.1.5 Bash-Skripte für Automatisierung

Bash-Skripte werden in den GitLab Pipelines verwendet, um automatisierte Aufgaben wie das Deployment der Anwendung auf EC2-Instanzen durchzuführen. Diese Skripte ermöglichen eine effiziente Verwaltung und Automatisierung von Entwicklungs- und Bereitstellungsprozessen innerhalb der Projektumgebung.

## 4.1.6 Python für Backend-Logik und Datenverarbeitung

Python wird für die Entwicklung der Backend-Logik verwendet. Dies umfasst die Implementierung von Geschäftslogik für Aufgabenverwaltung, Benutzerverwaltung und Authentifizierung. Python wird auch für Datenverarbeitungsaufgaben wie Validierungen von Benutzereingaben und die Verarbeitung von API-Anfragen eingesetzt.

## 4.1.7 REST API für Kommunikation

Die Anwendung wird eine RESTful API bereitstellen, die es ermöglicht, über standardisierte HTTP-Methoden wie GET, POST, PUT und DELETE mit der Anwendung zu interagieren. Die API wird klare Endpunkte definieren, um Aufgaben zu verwalten, Benutzer zu authentifizieren und Daten zwischen dem Frontend und dem Backend auszutauschen. Die Kommunikation erfolgt dabei über JSON als primäres Datenformat.

## 4.1.8 Technologiebeschreibungen

- **API Flask:** Flask wird verwendet, um eine robuste RESTful API zu entwickeln, die die Hauptfunktionalitäten der Anwendung bereitstellt. Dazu gehören Endpunkte für die Verwaltung von Aufgaben und Benutzern.
- **email_validator:** Ein Python-Paket zur Validierung von E-Mail-Adressen innerhalb der Benutzerverwaltung und Registrierungsprozesse.
- **Flask-SQLAlchemy:** Eine Flask-Erweiterung, die die Nutzung von SQLAlchemy erleichtert, um Datenbankschemas zu definieren und mit der MySQL-Datenbank zu interagieren.
- **Flask-WTF:** Eine Erweiterung für Flask, die die Erstellung und Validierung von Webformularen unterstützt, um Benutzereingaben zu verarbeiten.
- **Gunicorn:** Ein HTTP-Server für Python-Anwendungen, der als WSGI-Server fungiert und die Anwendung in der Produktionsumgebung betreibt.
- **PyMySQL:** Eine reine Python-Implementierung der MySQL-Datenbankzugriffsschnittstelle, die für die Kommunikation mit der RDS-Datenbank verwendet wird.
- **requests:** Eine einfache HTTP-Bibliothek für Python, die für den Zugriff auf externe APIs oder Dienste verwendet wird, z.B. für die Integration externer Dienste oder Datenquellen.
- **Werkzeug==3.0.1:** Eine WSGI-Bibliothek für Python, die von Flask verwendet wird, um HTTP-Anfragen zu verarbeiten und Routing-Funktionalitäten bereitzustellen.
- **WTForms:** Ein flexibles Formularvalidierungs- und Rendering-System für Python, das in Kombination mit Flask-WTF zur Validierung von Benutzereingaben verwendet wird.
- **mysql-connector-python:** Ein Python-Connector für MySQL-Datenbanken, der für die Verbindung und Ausführung von SQL-Abfragen innerhalb der Anwendung genutzt wird.
- **Flask-Migrate:** Eine Flask-Erweiterung für Datenbank-Migrationen, die hilft, Datenbankschemata einfach zu verwalten und zu aktualisieren, insbesondere während der Entwicklung und Skalierung der Anwendung.
- **Beautiful Soup (bs4):** Eine Bibliothek für das Scraping von Informationen aus Webseiten, die zur Verarbeitung und Extraktion von Daten aus externen Quellen verwendet werden kann, um Inhalte oder Informationen zu analysieren.

## 4.1.9 Sicherheit und Datenschutz

### Sicherheit

Da die Applikation nicht einer gewissen Größe entspricht, liegt der Fokus vor allem auf den Daten der Benutzer. Aus diesem Grund müssen Passwörter gehasht werden, bevor sie in die Datenbank gespeichert werden. Dies verhindert, dass bei einem Datenleck Passwörter im Klartext eingesehen werden können.

Zusätzlich müssen die Docker-Instanzen auf mögliche Schwachstellen untersucht werden. Aufgrund der Schulung von Marcel Bernet würde ich, falls diese Applikation produktiv verwendet wird, auf Podman wechseln. In diesem Projekt gehe ich jedoch noch nicht auf diese Schwachstellen ein.

### Datenschutz

Um den Datenschutzanforderungen gerecht zu werden, werden nur die nötigsten Daten in der Datenbank gespeichert. Aus diesem Grund beschränkt sich die Speicherung der Nutzerdaten auf das Minimum (E-Mail/Hashed Passwort).

Falls diese Applikation in den produktiven Zustand versetzt wird, muss anhand der Datenschutzgesetzverordnung dem Benutzer noch die Möglichkeit zur Löschung der Daten angeboten werden.
